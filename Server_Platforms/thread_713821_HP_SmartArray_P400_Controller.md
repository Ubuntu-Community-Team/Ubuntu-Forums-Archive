---
title: "HP SmartArray P400 Controller"
date: 2008-03-03
forum: Server Platforms
---

### Post by hendrikp on 2008-03-03
Hi Folks,

we are about to install Ubuntu Server 8.10 LTS (i know it's not stable yet...) on a HP SmartArray P400 based HP server. HP website tells us there is support for RHEL and Suse, buit we'd like Ubuntu Server. Can anyone tell us if the CCISS driver ([this]("http://cciss.sourceforge.net/") one) will be delivered with 8.10 LTS?

Thanks,

Hendrik

---

### Post by Petersonz on 2008-03-13
Im not an Ubuntu kernel developer, but I can tell you that the cciss driver in 2.6.24-11-server kernel with Hardy has serious issues with the p400i in my dl360 and dl380 G5's.

High CPU load, low I/O performance, etc.

Cant you just compile the latest cciss drivers as a module after installing the kernel-dev package? I havent tried that yet myself.

Of course, if HP is like Dell and only has Redhat/Suse drivers available, that might be tough to port.

---

