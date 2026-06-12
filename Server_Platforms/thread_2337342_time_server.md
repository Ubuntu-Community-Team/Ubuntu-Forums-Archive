---
title: "time server"
date: 2016-09-16
forum: Server Platforms
---

### Post by Vegan on 2016-09-16
I have ntp installed already so my virtual machine has the right time, I assume the defaults are fine as is

so what do i need to add to make this VM a cloud time server?

I am looking for using it with both Windows and Linux clients or servers

SOLUTION

open port 123 on the firewall and the defaults work fine.

the ntpd has defaults setup and it can figure out if there is any drift etc

---

### Post by TheFu on 2016-09-17
Running a time server on a VM is a really, really, bad idea. There are numerous references to back this up. ntp needs to be run on real hardware.  People use raspberry-pis for this, if they don't want to use a used, refurbed, $75 PC.

---

### Post by Vegan on 2016-09-19
can the raspberry run linux server ok?

---

### Post by TheFu on 2016-09-19
> **Vegan said:**
> can the raspberry run linux server ok?

Answer: [https://askubuntu.com/questions/212346/can-a-raspberry-pi-run-ubuntu](https://askubuntu.com/questions/212346/can-a-raspberry-pi-run-ubuntu)

My r-pi is busy running OSMC (really Kodi + PlexBMC on a Debian system). Plex Server runs on a $120 Pentium G3258-based system (parts used for case, PSU, RAM, HDDs) running Ubuntu server 14.04.x.  I wouldn't try to run a 500-user web app on a r-pi, but for most homes, a R-Pi v2 has more than enough power to run email, web, NTP, and perhaps ownCloud (if you don't abuse it).  Basically things that don't need much I/O.  

Inside a data center, they should already have NTP servers available and with VMs, getting accurate time should be handled by the VM-host. Review the documentation about this.  Usually, the guests get their time from the host using "extensions", so you and I shouldn't need to run NTP at all.  Use those.   Seems Azure is failing at this: [https://stackoverflow.com/questions/6138955/clock-synchronization-quality-on-windows-azure](https://stackoverflow.com/questions/6138955/clock-synchronization-quality-on-windows-azure)

At home, it is useful to have your own NTP if you have systems that can't keep time - like my Windows systems. They lost time constantly - enough that TV recordings missed parts of shows - which is really the only reason I still have Windows at all. The exact same machines running Linux are 10 ms accurate. Keeping correct, accurate, time has been something I've had issues with Windows since Win95.  I don't know why, just know that in a F-10 corporation where we had 3 MSFT corporate engineers located on-site, they said that Windows only needs time to be +/-5 min accurate, so that was  their target.  At my home, Windows was losing 5 min/hr until I setup an NTP server and modified the registry to force sync every 15 minutes.  Daily sync wasn't sufficient. Hourly sync wasn't either. I tried. Doing that with public time servers will get you banned.  A r-pi will be sub-second accurate, which is sufficient for everything I need (and most people).  R-pi v2 can be used for things that don't need heavy I/O - don't use for backup servers or pushing data around because the system architecture shares 1 I/O bus for everything ... USB, network, everything.  A cheap x86 (AMD/Intel) $50 CPU will provide 10,000x more I/O capacity than a R-Pi. 

Lots of unnecessary background. About my time issues: [http://blog.jdpfu.com/2010/01/16/solved-clock-time-loss-under-windows7-and-vista](http://blog.jdpfu.com/2010/01/16/solved-clock-time-loss-under-windows7-and-vista)

---

### Post by Vegan on 2016-09-19
I mostly put ntp on the box so it would have a reasonable idea what the real time is, better than to depend on some hypervisor that may not even now what day it is

windows is notorious for being out of whack with the right time, windows 10 still does not have a strong time manager that I have noticed

---

