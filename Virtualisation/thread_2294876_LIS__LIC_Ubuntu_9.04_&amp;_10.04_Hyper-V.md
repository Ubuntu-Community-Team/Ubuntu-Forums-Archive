---
title: "LIS / LIC Ubuntu 9.04 &amp; 10.04 Hyper-V"
date: 2015-09-14
forum: Virtualisation
---

### Post by gva24 on 2015-09-14
Hello community !

I have in my laboratory by testing some systems to go .

I found that in my Hyper - V 2012 (win 2012 R2) need the LIC / LIS Ubuntu 9.04 and 10.04.

How could I get ? I 've been watching and reading several issues that relate about it :
" In summary , the Integration Components are Already part of the 2.6.32 Linux Kernel , AT LEAST Quoting in Ubuntu 10.04 . :

Add the following to / etc / initramfs -tools / modules

hv_vmbus

hv_storvsc

hv_blkvsc

hv_netvsc
Generate a new initrd image

update- initramfs -u
make sure / etc / network / interfaces is pointed at the synthetic network adapter

auto seth0

seth0 inet dhcp iface "


Relizando said sequence of command would get the LIC / LIS last for these versions of ubuntu ?

Thank you

---

### Post by TheFu on 2015-09-14
Support for both those releases ended. Sorry.  
10.04 desktop support ended in 2013 and server support ended in April 2015
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The current LTS release with 5 yrs of support is 14.04.

I don't understand what "LIC/LIS" is. Sorry.

BTW, the correct form of the networking file is:```

iface eth0 inet dhcp
```  the order is important.

---

