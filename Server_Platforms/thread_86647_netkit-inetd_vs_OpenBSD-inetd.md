---
title: "netkit-inetd vs OpenBSD-inetd"
date: 2005-11-05
forum: Server Platforms
---

### Post by dutler on 2005-11-05
Ok, looks like we have at lease two standard choices for internet servers, netkit-inetd and OpenBSD-inetd. From the package distribtions the BSD sounds much better, but from teh Unbuntu Forms it seem users prefer netkit. What are your thoughts?

netkit-inetd |The Internet Superserver
The inetd server is a network daemon program that specializes in managing
incoming network connections. It's configuration file tells it what
program needs to be run when an incoming connection is received. Any
service port may be configured for either of the tcp or udp protcols.

OpenBSD-inetd | The OpenBSD Internet Superserver
The inetd server is a network daemon program that specializes in managing
incoming network connections. Its configuration file tells it what
program needs to be run when an incoming connection is received. Any
service port may be configured for either of the tcp or udp protcols.

This is a port of the OpenBSD daemon with some debian-specific features.
This package does not have many bugs of netkit-inetd and supports IPv6,
built-in libwrap, binding to specific addresses, UNIX domain sockets and
socket buffers tuning.

---

