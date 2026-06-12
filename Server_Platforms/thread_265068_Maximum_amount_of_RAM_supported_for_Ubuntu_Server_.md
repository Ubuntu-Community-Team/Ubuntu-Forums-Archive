---
title: "Maximum amount of RAM supported for Ubuntu Server 6.06"
date: 2006-09-25
forum: Server Platforms
---

### Post by Icereval on 2006-09-25
Can anyone point me to any documentation specifying the maximum amount of RAM allowed on an Ubuntu Server 6.06 install?

Also is there anything special required to setup the server to recognize an amount of RAM over 4GB?

I would like to use Ubuntu for its low maintenance on a new virtualization server I am receiving which has the capability of up to 64GB of RAM.

Thank You,

Michael

---

### Post by tuxthepenguin on 2006-09-25
Well looking at the current 2.6.18 kernel configuration linux supports 4Gb. But I swear not long ago there was an option for system with a lot more memory (64GB or so) I dont see it anymore.

---

### Post by fnjordy on 2006-09-25
Generally you need a 64-bit system to support over 4 GB system memory.  From 3-4 GB you might need a special kernel on 32 bit systems as the address space is usually reserved for system features (memory mapping, etc).  4GB is the largest number in 32 bit math, hence the limitation.  RedHat have a special custom kernel with highmem_io support for > 4GB, this is work especially done for RedHat Enterprise Linux and hence not well propogated to other distributions.

* [http://safari.oreilly.com/0131470248/app05lev1sec13](http://safari.oreilly.com/0131470248/app05lev1sec13)
* [http://www.redhat.com/rhel/details/limits/](http://www.redhat.com/rhel/details/limits/)

---

### Post by Icereval on 2006-09-26
So as long as I have bought 64-bit processors, and I install the 64-bit version of Ubuntu Server, I should have no issue with over 4GB of RAM.

---

