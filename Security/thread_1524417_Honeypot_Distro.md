---
title: "Honeypot Distro"
date: 2010-07-05
forum: Security
---

### Post by andremta on 2010-07-05
Is there any honeypot-ready distro?

I want to monitor my network

---

### Post by cariboo on 2010-07-05
Just so that we are on the same page, this is the definition of a [honeypot]("http://en.wikipedia.org/wiki/Honeypot_(computing)").

---

### Post by robots.jpg on 2010-07-06
This isn't exactly what you're asking for, but I run [Honeyd]("http://www.honeyd.org/index.php") on a clean install of  Ubuntu Server 10.04.  It can create virtual honeypots on any address or  range of addresses, or even create an entire virtual network.

If you download 1.5c release from that site, I'd  recommend dropping the updated honeyd.c file into your uncompressed  source directory before you compile so it doesn't ignore the -u and -g arguments:

[http://code.google.com/p/honeyd/source/browse/trunk/honeyd/honeyd.c](http://code.google.com/p/honeyd/source/browse/trunk/honeyd/honeyd.c)

You'll also need to use farpd or something similar to claim the addresses you  want your honeypot machines to use.


I hope others can recommend some different options for you.

---

