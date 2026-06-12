---
title: "HELP - Can't boot up OVH server running 14.04 - Kernel panic not syncing"
date: 2017-10-31
forum: Virtualisation
---

### Post by dinosaur3 on 2017-10-31
I can't boot into my OVH server running 14.04. I booted it into recovery mode and then installed QEMU and attempted to boot into it with VNC.

I'm getting this error:

[IMG]https://i.imgur.com/i6UCDkb.png[/IMG]

Transcript: Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
Bunch of text under that.

[B]What I've tried so far, in addition to the VNC attempt:
[/B]- Mounting the partition and chrooting into it, which doesn't have DNS resolution capabilities meaning that installing software like Boot-Repair isn't possible
- grub-mkconfig, grub-install from recovery system - no effect.
- Setting root and other info from grub recovery
- Boot info script ([results here]("https://pastebin.com/JRcSTLnU"))


[B]How can I recover my OS without having to re-install the OS? 

[/B]It's a 2TB disk, 2 partitions, and I *really* don't want to go through the hassle of disk dumping, backups, etc.

Any suggestions are welcome.

---

### Post by deadflowr on 2017-10-31
*Thread moved to **Virtualisation***

---

