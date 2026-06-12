---
title: "Upgrading Samba"
date: 2018-07-17
forum: Server Platforms
---

### Post by jdcowpland on 2018-07-17
I have an Ubuntu Server that hasn't been upgraded in ages. It's still running 12.04, so I plan on upgrading it to 16.04. It's primarily used as a Samba File Share and i notice that Ubuntu will upgrade samba from version 3.5.25 to 4.3.11. Does anyone know where I can find any help in checking over my configuration to make sure that it will all still work after performing the upgrade?

---

### Post by slickymaster on 2018-07-17
Thread moved to **Server Platforms** for a better fit

---

### Post by TheFu on 2018-07-17
Welcome to the forums.

For critical services, the best solution is to test the upgrade multiple times using a virtual machine, so you can minimize the actual issues and downtime when you perform the real upgrade to the production system.  It isn't just samba that has changed. Many core parts of networking and authentication are different.

---

### Post by jdcowpland on 2018-07-17
Yeah I'm working on the virtual machine side of things already. Currently testing the MySQL side of things but I managed to find the change logs for that and the various things that are incompatible between versions, so if things fail in the test environment, I at least know where to start looking. I was hoping I would be able to do the same with Samba.

---

### Post by TheFu on 2018-07-17
samba.org - google found this:
[https://wiki.samba.org/index.php/Samba_Features_added/changed_(by_release)](https://wiki.samba.org/index.php/Samba_Features_added/changed_(by_release))
But you will still need to test since interactions and specific settings that each instance has can change things.

---

### Post by jdcowpland on 2018-07-17
Yup, I saw that and was daunted by the long list... Guess there's no shortcuts :P I'll test on the virtual server and if I encounter any issues I'll just use google.

---

### Post by LHammonds on 2018-07-17
I manage over a dozen Linux servers and have gone through upgrades from 10.04 -> 12.04 -> 14.04 -> 16.04 and now I am currently going to 18.04.

I have never found that doing an in-place upgrade to ever go smoothly.  Not because the OS did not upgrade correctly but because the additional apps (PHP 5->7, etc.) and the various complications such as data and configuration files needing to be updated/changed after upgrade.  Sometimes needing to swap to different software to maintain functionality.

All this is NOT something you want to find out after upgrading your OS.  I like to have downtime minimized to the timespan of a reboot (usually to swap IP addresses with the new/old servers).

I find that it works best by installing the new OS on a new machine (such as a virtual machine on your desktop) and then install the desired software and configure it to work like your old server.  This is also a perfect opportunity to document how this is done if it was not done before...which makes future upgrades even faster/easier.

If you are working with virtual machines, this is a VERY easy process.  If you are working on physical machines, it takes a bit longer but you can still do it with very little downtime.  You just have to do 2 migrations...first is the migration/upgrade to the new version in a virtual machine (like your PC).  The last is re-formatting the original physical server and installing it fresh like you did the VM and simply migrate the data/settings from the VM back to the physical server.

As you can see from my sig, I like to document how I setup my servers which makes it MUCH easier when doing the same on a new version of the OS.  There might be some library names that are different but will be easy to search/update my documentation on what the new names are (example: php7.0-mysql -> php7.2-mysql)

LHammonds

---

### Post by 1madlad on 2019-05-05
Thanks for this post and the link to install Ubuntu Server in your sig. I was having some issue getting Samba to work and I with to your link and read through it and was able to figure out my problem and now I have everything working well thanks to you.

Again Thanks,

-Madlad

---

### Post by LHammonds on 2019-05-07
> **1madlad said:**
> Thanks for this post and the link to install Ubuntu Server in your sig. I was having some issue getting Samba to work and I with to your link and read through it and was able to figure out my problem and now I have everything working well thanks to you.

Again Thanks,

-MadladI'm pleased to hear you got it working!  Good job!

---

