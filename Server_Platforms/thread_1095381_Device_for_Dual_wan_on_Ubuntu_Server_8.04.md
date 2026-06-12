---
title: "Device for Dual wan on Ubuntu Server 8.04"
date: 2009-03-13
forum: Server Platforms
---

### Post by orhanaslan on 2009-03-13
Hi everyone,

I am new user on Ubuntu server and all I can say Ubuntu is great. I have an issue regarding dual wan.

Our school has 1 ADSL line at this moment and we have installed a server which is Ubuntu Server 8.04 and this server filtering our internet and our modem configured in bridge mode.

Now we need second internet access but lots of think is unclear and I could not find appropriate documents yet.

Coudl you help me to make it clar please?


Regards

---

### Post by orhanaslan on 2009-03-20
Waoww no response yet. Is it hard for linux guys? No solution for dual adsl?

---

### Post by netztier on 2009-03-20
> **orhanaslan said:**
> Waoww no response yet. Is it hard for linux guys? No solution for dual adsl?

Dual WAN is more complex than one might think, so I suggest to do a bit of research and reading:

[http://www.netlife.co.za/content/view/47/34/](http://www.netlife.co.za/content/view/47/34/)

regards

Marc

---

### Post by windependence on 2009-03-20
> **orhanaslan said:**
> Waoww no response yet. Is it hard for linux guys? No solution for dual adsl?

Simple. [http://www.pfsense.com/](http://www.pfsense.com/)

You can set up multiple WANs right in the web GUI.

-Tim

---

### Post by HermanAB on 2009-03-21
If you want to know how it works, read the Advanced Routing Howto on [http://www.tldp.org](http://www.tldp.org) about five to ten times.  

Here is a DIY description:
[http://aeronetworks.ca/doublebarrel.html](http://aeronetworks.ca/doublebarrel.html)

It is not exactly simple.

Cheers,

Herman

---

### Post by windependence on 2009-03-21
Well it may not be simple on Linux, but on FreeBSD with pfsense it's easy and all web GUI:

[http://doc.pfsense.org/index.php/MultiWanVersion1.2](http://doc.pfsense.org/index.php/MultiWanVersion1.2)

-Tim

---

### Post by orhanaslan on 2009-03-23
Thanks guys at least some infos so much better than nothing. I'll check it out the web sites taht yo have put here.

Regards

---

