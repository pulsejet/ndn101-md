# Getting Started

This page will guide you through the process of installing the basic tools needed to start using and developing NDN applications.

## Packet Forwarder

To begin, you will need to first install the **NDN Forwarding Daemon (NFD)** on your computer.
There are several implementations of NFD, the most popular of which are:

  * [NFD](https://docs.named-data.net/NFD/current/INSTALL.html)[@afanasyev2014nfd], the reference implementation (C++)
  * [YaNFD](https://github.com/named-data/yanfd)[@icn2021yanfd], a multithreaded implementation (Golang)
  * [NDN-DPDK](https://github.com/usnistgov/ndn-dpdk)[@icn2020dpdk], a high-performance implementation (C)
  * [NDN-Lite](https://github.com/named-data-iot/ndn-lite)[@icn2018ndnot], an IoT implementation (C)

!!! tip "What is the role of NFD?"
    NFD is the NDN equivalent of an IP "router", and runs on _each node_ in the network.
    It is responsible for forwarding NDN packets between nodes, including functions of Data multicast and caching.

## Client Library

Next, you will need to install a **client library** of your choice to interact with the NDN network.
Depending on the library, you will need the corresponding compilers / interpreters / build tools.

  * [ndn-cxx](https://github.com/named-data/ndn-cxx) (C++) [[Docs](https://docs.named-data.net/ndn-cxx/current/INSTALL.html), [API](https://docs.named-data.net/ndn-cxx/current/doxygen/annotated.html)]
  * [python-ndn](https://github.com/named-data/python-ndn) (Python) [[Docs](https://python-ndn.readthedocs.io/en/latest/)]
  * [NDNts](https://github.com/yoursunny/NDNts) (TypeScript) [[Docs](https://yoursunny.com/p/NDNts/)]
  * [go-ndn](https://github.com/zjkmxy/go-ndn) (Golang)
  * [NDN-Lite](https://github.com/named-data-iot/ndn-lite) (C, IoT) [[Docs](https://github.com/named-data-iot/ndn-lite/wiki), [API](https://zjkmxy.github.io/ndn-lite-docs/index.html)]
  * [esp8266ndn](https://github.com/yoursunny/esp8266ndn) (Arduino) [[API](https://esp8266ndn.ndn.today/)]

!!! tip "What does the client library do?"

    The client library provides the NDN equivalent of a TCP/IP "socket", and runs inside _each application_.
    It is responsible for encoding and decoding NDN packets, and sending / receiving them to / from NFD.

Once you have installed NFD and a client library, you need to start NFD on your local development machine.
You are now ready to start developing NDN applications!

!!! info "Contributing to the NDN codebase"

    The NDN codebase is free and open-source software, and most of it is available on [GitHub](https://github.com/named-data). If you are interested in contributing, make sure you read [this guide](https://github.com/named-data/.github/blob/main/CONTRIBUTING.md) and the [code of conduct](https://github.com/named-data/.github/blob/main/CODE_OF_CONDUCT.md) first.

## Debugging Tools

The [ndn-tools](https://github.com/named-data/ndn-tools) package is highly recommended and contains several tools for developing and debugging NDN applications.

  * [peek](https://github.com/named-data/ndn-tools/tree/master/tools/peek): transmit a single Interest/Data packet between a consumer and a producer.
  * [chunks](https://github.com/named-data/ndn-tools/tree/master/tools/chunks): segmented file transfer between a consumer and a producer.
  * [ping](https://github.com/named-data/ndn-tools/tree/master/tools/ping): test reachability between two NDN nodes
  * [dump](https://github.com/named-data/ndn-tools/tree/master/tools/dump): capture and analyze live traffic on an NDN network
  * [dissect](https://github.com/named-data/ndn-tools/tree/master/tools/dissect): inspect the TLV structure of an NDN packet
  * [dissect-wireshark](https://github.com/named-data/ndn-tools/tree/master/tools/dissect-wireshark): Wireshark extension to inspect the TLV structure of NDN packets

!!! tip "Ping test for NFD"

    You can run a simple test for your local NFD by using thee ndn-tools package to start a ping server and client on the same machine. These will then communicate by connecting to NFD over a unix socket.

    ``` bash
    ndnpingserver /my/nfd/test &
    ndnping /my/nfd/test
    ```

## Getting Help

If you have any questions about NDN or the code base, we encourage you to reach out to the community for help.
Some options include,

  - Ask a question at the most appropriate [mailing list](https://named-data.net/codebase/platform/support/mailing-lists/).
  - File an issue at the relevant [GitHub](https://github.com/named-data) repository or [Redmine](https://redmine.named-data.net/projects).
  - (If applicable) reach out to the authors of the paper that introduced the software.
