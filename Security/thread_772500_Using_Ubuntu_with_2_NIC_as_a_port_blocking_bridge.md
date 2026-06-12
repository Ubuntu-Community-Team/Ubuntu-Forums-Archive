---
title: "Using Ubuntu with 2 NIC as a port blocking bridge"
date: 2008-04-28
forum: Security
---

### Post by Lem on 2008-04-28
I have part of a network running across a wifi mesh throughout a worksite. In normal operation I only need to use VNC and FTP to/from these PCs (ie. only ports 21 and 5600) but it would be useful to be able to temporarily turn any filter off if I need to send files or any other maintenance work.

Most firewalls work as routers so I'd have to have a different IP range on either side, which in this instance I'd rather not do.

My plan is to have a small pc with 2 NICS running as a bridged filter allowing only the FTP&VNC traffic to pass in normal operation. A web interface would be useful for my less linux-knowledgable colleagues to manage when I'm not here.

Any ideas on setup & software?

---

### Post by HermanAB on 2008-04-28
Read the Advanced Routing Howto on tldp.org.

Cheers,

Herman

---

