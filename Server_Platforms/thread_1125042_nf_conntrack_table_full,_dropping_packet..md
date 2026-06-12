---
title: "nf_conntrack: table full, dropping packet."
date: 2009-04-14
forum: Server Platforms
---

### Post by Innom on 2009-04-14
Hi All,

I'm currently using Ubuntu Hardy to host a rather busy FTP server.  As part of the firewall configuration, I've used nf_conntrack so that connections for PASV ftp are allowed.

I'm getting errors in my kernel logs indicating that the nf_conntrack table is full:

[475756.276021] nf_conntrack: table full, dropping packet.
[475759.309583] nf_conntrack: table full, dropping packet.
[475780.272422] nf_conntrack: table full, dropping packet.
[475812.177179] nf_conntrack: table full, dropping packet.
[475833.140108] nf_conntrack: table full, dropping packet.
[475871.111512] nf_conntrack: table full, dropping packet.
[475875.127547] nf_conntrack: table full, dropping packet.


Additionally, our monitoring systems are picking up, at corresponding times, that ICMP Pings are being dropped on this machine.

I've tried increasing the nf_conntrack limit to double it's default value of 65536, and cutting all the timeouts in half, but it seems no matter what I do, this limit is always reached.

I was wondering if there's some (potentially) obvious setting which might be causing nf_conntrack to maintain a few too many sessions, or some other known issue which can be worked around?

Thanks

---

