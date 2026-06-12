---
title: "nfs and ntp constantly loading during boot-up screen"
date: 2009-06-23
forum: Server Platforms
---

### Post by vtknightmare on 2009-06-23
Hello All:

I've created a monster I cannot fix, and am now waving the white-flag for help :)

Here's my problem:

Scenario: NFS and NTP were not installed/loaded on this Ubuntu 8.04 LTS (VM guest) server I maintain.

So I installed both via aptitude, then encountered problems with their loading order in the /etc/rc levels, so played around with update-rc.d and found a happy medium where nfs loaded after networking, and unloaded prior to networking killing, etc.

Well, this past weekend, I decided to maintain one of the apps on the server, and rebooted it. Upon coming up I noticed, it is now over and over trying to load nfs and ntp...

An ls -alF /etc/rc* shows that nfs-common loads on all levels plus rcS, and ntp is loading in rc5-1 (not in rc0, 6 or S)

Can someone help me by how to go about debugging and hopefully fixing this?

TIA!

---

### Post by vtknightmare on 2009-06-25
Is this issue really not worthy of a help-push?

---

### Post by vtknightmare on 2009-07-27
^^bump^^

---

