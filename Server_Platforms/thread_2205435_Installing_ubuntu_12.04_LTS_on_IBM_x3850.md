---
title: "Installing ubuntu 12.04 LTS on IBM x3850"
date: 2014-02-13
forum: Server Platforms
---

### Post by Marek_Knappe on 2014-02-13
Hey, 
I have some old stuff that want to use now for dev proposes, and wanted to install unbuntu on that. Server is:
IBM X3950 and it has 
(LSI-MFI) ServeRaid MR-10k

The problem is, that ubuntu installed cannot detect my raid HDD, so i tried to find the correct module, and according to that:
[http://manpages.ubuntu.com/manpages/precise/man4/mfi.4freebsd.html](http://manpages.ubuntu.com/manpages/precise/man4/mfi.4freebsd.html)
MFI is correct driver, but unfortunately there is no mfi on the installation cd. How i can install system on that hardware ?\

I also see that that controler and that server is supported here:
[http://www.ubuntu.com/certification/hardware/201102-7300/](http://www.ubuntu.com/certification/hardware/201102-7300/)

for version 10.04 LTS, but it's uncommon that newer version of ubuntu is not supporting older hardware.

---

### Post by Yellow Pasque on 2014-02-13
mfi is a BSD module.

You're probably looking for megaraid_sas, which should be in the kernel, though I don't know if it's enabled in Precise's kernel. [https://github.com/torvalds/linux/tree/master/drivers/scsi/megaraid](https://github.com/torvalds/linux/tree/master/drivers/scsi/megaraid)

---

### Post by Marek_Knappe on 2014-02-13
Hey, the megaraid_sas is not detecting any harddrives, tried already. It is enabled.
actually i even did:
cd /var/lib/modules/*3.*/drivers/devices/scsi or something like that and 
find --exec insmod {}\;

to check all drivers, but any of the one included one are not working :/

---

### Post by Bucky Ball on 2014-02-13
*Thread moved to **Server Platforms**.*

You could try 13.10. Yes, should _always_ use an LTS on a server but this might get you over a hump until 14.04 LTS is released in April. 13.10 is directly upgradeable to that after release.

Not that I'm thinking this is your problem, just a suggestion ...

---

