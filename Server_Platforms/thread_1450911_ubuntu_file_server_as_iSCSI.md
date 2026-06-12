---
title: "ubuntu file server as iSCSI??"
date: 2010-04-09
forum: Server Platforms
---

### Post by Isaacariah on 2010-04-09
Hi there

I've been toying with the idea of setting up a small home server, with services such as file server, website hosting, irc bnc etc and VPN support to access these over the internet.

What I was wondering however, was if there was a way, rather than have the file server as a network share on my LAN, could I setup some kind of system whereby my shared folders work as an iSCSI interface on my windows machines?

From what I can tell, iSCSI takes away some of the short comings of network file sharing, as these machines would see it as a physical drive rather than a mapped drive?

Unless I'm making wild speculation here, is it possible, or another way of having permanent shares set up on local machines in an iSCSI way, but also I'd need access to them via my VPN...

Thanks in advance

---

### Post by Cosma on 2010-04-10
there shouldn't be a problem mounting iscsi volumes on a windows computer (via vpn or direct). to connect more than one computer to a iscsi volume you need a cluster filesystem on it or you will destroy the data as soon as a other computer opens the volume.

i could think about some ways if you run linux but i am not aware of a cluster filesystem for microsoft...

better just go with samba.

---

### Post by fang0654 on 2010-04-11
I second this - iSCSI wouldn't be the right solution for you.  What shortcomings are you worried about running into?

---

