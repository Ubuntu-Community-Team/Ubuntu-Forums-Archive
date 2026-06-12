---
title: "Problem with adding a node to MAAS - Intel Boot Agent"
date: 2014-07-08
forum: Ubuntu Cloud and Juju
---

### Post by maciej7 on 2014-07-08
Hello,

I installed MAAS (Ubuntu 14.04 Server, x64) and just wanted to add node to it. But there is a problem, while booting i get information on the screen which says something like there is not a boot image. Also, I can't see node added with "Declare" status in my MAAS admin panel - seems like it isn't added... I have properly configured DHCP and DNS.

Here's a picture of part of my network:

[IMG]http://img856.imageshack.us/img856/7595/ugmx.png[/IMG]

There is STP (Rapid STP) on my Switch, but ports (those, where MAAS and Node are connected) are in Port Fast mode. Node get IP from DHCP.

---

### Post by peterwilson-69 on 2014-10-03
Is there specific errors in the log files? Check the following locations.

```
/var/log/maas
```

---

