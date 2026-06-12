---
title: "raring panics after BIOS upgrade"
date: 2013-01-15
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-01-15
Spending some time updating a BIOS on an Intel Desktop Board 266GHz Dual Core /1.5GB DDR2/500GB SATA from gc11010n.86a.0303 to 0313 back to 0307. Maveric and Quantal work fine but Raring 3.8.0-0 will only boot after choosing recovery option in GRUB and when it does boot it runs like molases.

---

### Post by ventrical on 2013-01-15
I was able to get it running with 3.5.0-18 kernel but anything from 7.7.0-0 and up won't run unless ran through the recovery script.

---

### Post by zika on 2013-01-16
First shot in the dark: AHCI is turned on?

---

### Post by ventrical on 2013-01-16
> **zika said:**
> First shot in the dark: AHCI is turned on?


It's not there. In the BIOS .. it's not there. Thats why I upgraded the BIOS and it is still not there. However I  got my hardware system back .. but anything 3.7 and above  will only boot in recovery . I even tried reinstalling some of those kernels and installed the /current/ kernel from the ppa .. but it appears to load the kernel on the purple screen and just locks up.

  Are you speaking of a mehtod that the AHCI can be turned on in software?

---

### Post by ventrical on 2013-01-21
Just updating  on the BIOS problem.  I tried to do a fresh install on the affected partiton. Raring installed OK but there are lots of ata errors .. sort of like it cannot find the SATA drive and when it does it finally boots . The fresh install is as slow as molases but the  three other installs I have , 2 quantal and 1 Maveric , are all working just fine. I did back up my folders. 

  This more or less is something that I did. Pilot error. I am not declaring that this is an Ubuntu problem. Obviously there is  some hardware interupt conflicts that I will have to work with. 

  I tired to find the original BIOS from Intel but it does not look like it is  available. 

gc11010n.86a0303

 Raring was working just fine on that.

 Because I most likely borked my own system I am going to mark this thread as solved.

:)

---

### Post by dino99 on 2013-01-21
AS a new FWTS version has been released, i've made a test on my system, and have had a bunch of acpi errors and also AMLAssemblerErrors on that updated RR i386

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1102370](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1102370)

---

### Post by ventrical on 2013-01-21
> **dino99 said:**
> AS a new FWTS version has been released, i've made a test on my system, and have had a bunch of acpi errors and also AMLAssemblerErrors on that updated RR i386

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1102370](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1102370)

Dino99,

Thanks!

  I decided to install over the borked raring (daily) install from a 12.04 USB stick and it was a seamless install. 

  I am going to unmark this thread as 'solved.'  Ubiquity in raring (daily) is not installing correctl at all. Precise had no problem with those errors.. so it is not BIOS update.

---

