---
title: "Server won't recognize 2nd Hard drive after reboot"
date: 2010-08-05
forum: Server Platforms
---

### Post by 1serveyou on 2010-08-05
Hi guys, I thought I was doing great with ubuntu, but this last time I turned off the server and turned it back on, the 2nd won't work. I've tried sudo lshw -C disk, and no luck on seeing the drive. I thought it was bad, but when I plugged it into an enclosure and plugged it into my linux laptop it saw it immediately. I can't find anyway for linux to recognize or see the drive. Any help would greatly be appreciated. I know it's probably something real easy, but for some reason I can't figure it out.

When I run sudo fdisk -l, it only shows SDA's for a few seconds, and then it scrolls(count down saying 16820 @ 0 for 0, type=0x0, 16821 @ 0 for 0, type=0x0, and then it says Segmentation fault.

---

### Post by pipemartinm on 2010-08-05
What's it formated with? ext3/4? Is it listed under /dev?

---

### Post by 1serveyou on 2010-08-09
> **pipemartinm said:**
> What's it formated with? ext3/4? Is it listed under /dev?

ext3

---

### Post by sauma on 2011-09-03
I'm having this exact issue. I put a 1tb drive in my media server and couldn't format it with gparted (however it did show up). When I run sudo fdisk -l I get the same problem. 

I'm running 10.10 ppc.

---

