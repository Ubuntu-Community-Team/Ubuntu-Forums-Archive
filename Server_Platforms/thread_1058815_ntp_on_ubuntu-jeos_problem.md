---
title: "ntp on ubuntu-jeos problem"
date: 2009-02-03
forum: Server Platforms
---

### Post by michas84 on 2009-02-03
hi,
I have ubuntu v 8.04.1 wirtualized on xen in my comapy, it stands for small http and nagios server, and I have ntp server for my company on another machine, not wirtualized. now what happens, all the machines in the company are synchronizing with this ntp server, but the ubuntu is not. I can see that they're talking to each other (tcpdump), I can see my ntp server in "ntpq -p", but it ignores it. config file is same on all the machines (except windows ;) and the only problem is with ubuntu. I've tried to add following option to kernel in grub config file (/boot/grub/menu.lst):
```
clocksource=acpi_pm
```
but it doesn't work. any ideas?

regards, michas

P.S.
and there's no "/proc/sys/xen/independent_wallclock" file; not even the "/proc/sys/xen/" directory... I see "/proc/sys/vm" directory instead, but there's no file with "clock" in it's name.

---

### Post by michas84 on 2009-02-05
more feedback:
ubuntu is synchronizig when I stop the ntp daemon and enter:
```
ntpdate 192.168.4.1
```
where 192.168.4.1 is my local ntp server. From then ubuntu's clock is slowing down, about 16 hours later I am 20 seconds behind, and the gap is growing. I tried to use chrony instead of ntp, but there's no effect. The Dom0 machine is solaris and it's synchronizng with that ntp server as well, it works fine. the only problem is with that ubuntu. still no idea what to do...

regards,
michal

---

