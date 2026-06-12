---
title: "Setup tor, install conflict"
date: 2011-10-28
forum: Security
---

### Post by Frozen Forest on 2011-10-28
I have looked at these guides
[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)
[https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

After adding the repository, did I get this conflict, I guess the last one is from the added repo but how do I install that one. Also noticed that this package is in conflict with libssl0.9.8, is this a problem? Is there a better way to setup tor?

```

Package: tor
Priority: optional
Section: universe/net
Installed-Size: 2184
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Peter Palfrader <weasel@debian.org>
Architecture: amd64
Version: 0.2.1.30-1build2
Depends: libc6 (>= 2.7), libevent-2.0-5 (>= 2.0.10-stable), libssl1.0.0 (>= 1.0.0), zlib1g (>= 1:1.1.4), adduser, tsocks
Recommends: polipo (>= 1) | privoxy, socat, logrotate, tor-geoipdb
Suggests: mixmaster, mixminion, anon-proxy
Conflicts: libssl0.9.8 (<< 0.9.8g-9)
Filename: pool/universe/t/tor/tor_0.2.1.30-1build2_amd64.deb
Size: 1099174
MD5sum: 5f11b052134b721877dec6363e2ca1c0
SHA1: b2da7b8a862e2ef388845e812b297b813eb1f671
SHA256: 2534f3540951c5c755e42fccac0ab51d121ad8b56ae3a16dd656104b66d3c538
Description-en: anonymizing overlay network for TCP
 Tor is a connection-based low-latency anonymous communication system which
 addresses many flaws in the original onion routing design.
 .
 In brief, Onion Routing is a connection-oriented anonymizing communication
 service. Users choose a source-routed path through a set of nodes, and
 negotiate a "virtual circuit" through the network, in which each node
 knows its predecessor and successor, but no others. Traffic flowing down
 the circuit is unwrapped by a symmetric key at each node, which reveals
 the downstream node.
 .
 Basically Tor provides a distributed network of servers ("onion
 routers"). Users bounce their tcp streams (web traffic, ftp, ssh, etc)
 around the routers, and recipients, observers, and even the routers
 themselves have difficulty tracking the source of the stream.
 .
 Note that Tor does no protocol cleaning.  That means there is a danger that
 application protocols and associated programs can be induced to reveal
 information about the initiator.  Tor depends on Privoxy and similar protocol
 cleaners to solve this problem.
 .
 Client applications can use the Tor network by connecting to the local
 onion proxy.  If the application itself does not come with socks support
 you can use a socks client such as tsocks.  Some web browsers like mozilla
 and web proxies like privoxy come with socks support, so you don't need an
 extra socks client if you want to use Tor with them.
 .
 This package enables only the onion proxy by default, but it can be configured
 as a relay (server) node.
 .
 Remember that this is development code -- don't rely on the current Tor
 network if you really need strong anonymity.
 .
 The latest information can be found at [https://www.torproject.org/](https://www.torproject.org/), or on the
 mailing lists, archived at [http://archives.seul.org/or/talk/](http://archives.seul.org/or/talk/) or
 [http://archives.seul.org/or/announce/](http://archives.seul.org/or/announce/).
Homepage: [https://www.torproject.org/](https://www.torproject.org/)
Description-md5: f1015a96c6ab0e71d6d9129f07bbcba1
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Package: tor
Version: 0.2.2.34-1~oneiric+1
Architecture: amd64
Maintainer: Peter Palfrader <weasel@debian.org>
Installed-Size: 2157
Depends: libc6 (>= 2.8), libevent-1.4-2 (>= 1.4.14b-stable), libssl1.0.0 (>= 1.0.0), zlib1g (>= 1:1.1.4), adduser
Recommends: logrotate, tor-geoipdb, torsocks | tsocks
Suggests: mixmaster, xul-ext-torbutton, socat, tor-arm, polipo (>= 1) | privoxy
Conflicts: libssl0.9.8 (<< 0.9.8g-9)
Homepage: [https://www.torproject.org/](https://www.torproject.org/)
Priority: optional
Section: net
Filename: pool/main/t/tor/tor_0.2.2.34-1~oneiric+1_amd64.deb
Size: 1030936
SHA256: 2de3a79a78625e6909a943792e6f304e57c78d22543e0ead5584ca9ec241fda9
SHA1: f6c8fd42eedb4c65677159f962279cd90f26f4bf
MD5sum: b01a14f6beffe599949f151366ab6120
Description: anonymizing overlay network for TCP
 Tor is a connection-based low-latency anonymous communication system which
 addresses many flaws in the original onion routing design.
 .
 In brief, Onion Routing is a connection-oriented anonymizing communication
 service. Users choose a source-routed path through a set of nodes, and
 negotiate a "virtual circuit" through the network, in which each node
 knows its predecessor and successor, but no others. Traffic flowing down
 the circuit is unwrapped by a symmetric key at each node, which reveals
 the downstream node.
 .
 Basically Tor provides a distributed network of servers ("onion
 routers"). Users bounce their tcp streams (web traffic, ftp, ssh, etc)
 around the routers, and recipients, observers, and even the routers
 themselves have difficulty tracking the source of the stream.
 .
 Note that Tor does no protocol cleaning.  That means there is a danger that
 application protocols and associated programs can be induced to reveal
 information about the initiator.  Tor depends on Privoxy and similar protocol
 cleaners to solve this problem.
 .
 Client applications can use the Tor network by connecting to the local
 onion proxy.  If the application itself does not come with socks support
 you can use a socks client such as tsocks.  Some web browsers like mozilla
 and web proxies like privoxy come with socks support, so you don't need an
 extra socks client if you want to use Tor with them.
 .
 This package enables only the onion proxy by default, but it can be configured
 as a relay (server) node.
 .
 Remember that this is development code -- don't rely on the current Tor
 network if you really need strong anonymity.
 .
 The latest information can be found at [https://www.torproject.org/](https://www.torproject.org/), or on the
 mailing lists, archived at [https://lists.torproject.org/pipermail/tor-talk/](https://lists.torproject.org/pipermail/tor-talk/) or
 [https://lists.torproject.org/pipermail/tor-announce/](https://lists.torproject.org/pipermail/tor-announce/).



```

---

