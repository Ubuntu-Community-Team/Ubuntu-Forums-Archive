---
title: "Monitor for FireFox  and other browsers"
date: 2009-03-04
forum: Security
---

### Post by mrl777 on 2009-03-04
I want to monitor what URLs Firefox connects to.  In other words, I want to make sure that the browser is not secretly connecting to an address.  So, I need a monitoring tool that can sniff the data stream and tell me what is going on, and even allow me to block outgoing and incoming connections.

The ultimate reason for this is to make sure the plug-ins and add-ons are behaving as advertised.

---

### Post by bodhi.zazen on 2009-03-04
Well, it it is a single IP, black list it with iptables.

If it is multiple IP, dansguardian ?

If you want to monitor your traffic, wireshark or snort.

---

