---
title: "monitor a service network traffic"
date: 2012-10-24
forum: Server Platforms
---

### Post by Minsk on 2012-10-24
I have setted up a tftp/nfs server on my Ubuntu 12.04 Server, to run as a PXE boot service.

However i am currently trying to make a nice looking webinterface to manage it, and 1 of the informations i want to show, is the current and overall used network traffic it has been hosting.

i was wondering if there is a way to get information on how much traffic NFS and TFTP is taking specificly?

---

### Post by anonymouschief on 2012-10-24
Try ntop

[http://www.ntop.org/products/ntop/](http://www.ntop.org/products/ntop/)

```
 sudo apt-get install ntop
```

---

### Post by Habitual on 2012-10-24
[http://www.nwsmith.net/HintsTips/net-snmp-tutorial.htm](http://www.nwsmith.net/HintsTips/net-snmp-tutorial.htm)

---

