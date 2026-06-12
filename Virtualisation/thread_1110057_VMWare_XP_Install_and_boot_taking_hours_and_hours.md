---
title: "VMWare XP Install and boot taking hours and hours??"
date: 2009-03-29
forum: Virtualisation
---

### Post by jonsamwell on 2009-03-29
Hi,

I have successfully installed vmware server 2 in ubuntu 8.10.

I started this morning installing a windows xp3 sp3 image and it took about 4 hours!!! Is this normal?

I restarted everything and tried to boot up xp in vmware for the first time, so far it is taken 1 hour!! I can hear the hard drive working over time, some thing has happened it is on the xp windows loading screen.

I am running ubuntu 8.10 on a quad core 2.66Mhz 2GB Ram and plenty of HDD space.

The xp image has 16GB HD and 2GB Memory.

Why is it taking so long??

Is this normal for the first boot and install?

Anyone have any ideas?

Also my system is quite unresponsive when it was install and trying to boot?

Thanks

Jon

---

### Post by veloce on 2009-03-31
> **jonsamwell said:**
> Hi,

I have successfully installed vmware server 2 in ubuntu 8.10.

I started this morning installing a windows xp3 sp3 image and it took about 4 hours!!! Is this normal?

I restarted everything and tried to boot up xp in vmware for the first time, so far it is taken 1 hour!! I can hear the hard drive working over time, some thing has happened it is on the xp windows loading screen.

I am running ubuntu 8.10 on a quad core 2.66Mhz 2GB Ram and plenty of HDD space.

The xp image has 16GB HD and 2GB Memory.

Why is it taking so long??

Is this normal for the first boot and install?

Anyone have any ideas?

Also my system is quite unresponsive when it was install and trying to boot?

Thanks

Jon

No, shouldn't take that long.

I would try making the virtual ram smaller than the physical.  vmware won't physically be able to provide 2Gb as some of it is used by the host so it is probably having to swap out your vm all the time.

Set it to 512Mb and see if it sorts it.

---

### Post by harish.chigurupati on 2009-05-29
hi veloce I also tried installing xp sp2 in vmware workstation 6.5.2. It took more than 5 hours to install. If you have solution to this problem please let me know. Thannks in advance.

---

