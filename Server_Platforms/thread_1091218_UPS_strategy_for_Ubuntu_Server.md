---
title: "UPS strategy for Ubuntu Server"
date: 2009-03-09
forum: Server Platforms
---

### Post by lopes_andre on 2009-03-09
Hi, I need to setup a server, using Ubuntu Server and I will use an UPS, for possible cut's of power.

I need to know if there is something that can do this... when power goes off, the server receives a command to shutdown the machine.

This is possible?

Best Regards, André.

---

### Post by drdub on 2009-03-09
If you have an APC UPS, this is (among other things) what apcupsd does.

For APC or other UPSes, I think nuts does the same. I have only used apcupsd however.

---

