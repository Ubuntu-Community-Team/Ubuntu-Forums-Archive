---
title: "VNC listen specific interface"
date: 2008-12-06
forum: Server Platforms
---

### Post by Shwick2 on 2008-12-06
I'm running ubuntu 8.04 with vnc4server.

I'm trying to get my vnc server to listen on a specific interface.  I don't want it listening on localhost, I want it listening on a virtual tun interface I setup, tun0, ip 10.6.7.0.

I tried adding the "-interface" option to the vnc4server script but Xvnc doesn't like it, "Unrecognized option: -interface".

How would I make vnc listen on a specific interface?

---

### Post by hictio on 2008-12-06
I don't use VNC, but I found this old post: [Binding to specfic interface (UNIX)](http://www.realvnc.com/pipermail/vnc-list/2002-April/029763.html), it's from 2002, and it's exactly your problem.
Can you setup an iptables rule on the server to stop connections to VNC from any other IP than the tun one? Will that work with iptables involved?

---

### Post by Shwick2 on 2008-12-07
Thanks that is exactly my problem- unfortunately the problem in that 2002 post wasn't solved :(.  I made a post on vnc mailing list, maybe that will help too.

Yes I could set up iptables to do that, but I would prefer to have vnc listen on a single interface and DNAT allowed interfaces to it.

---

