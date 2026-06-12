---
title: "Server boots to grub"
date: 2012-05-23
forum: Server Platforms
---

### Post by Sparticuz on 2012-05-23
I'm not too sure what's going on with my server. Yesterday, I rebooted the server and it booted up to grub. Screen says 'Minimal BASH-like .... etc'. I've tried pretty much every single thing I've found on the forums on reinstalling grub, but nothing is helping. I've tried booting to the Server rescue mode from the install disk and tried reinstalling grub. I've tried the Boot Rescue Disk, nope. I can get in and see all my files via the server rescue mode. But grub will not boot anything. No menu comes up, just the grub cli. I only have my boot drive plugged in. I've disconnected the other drives for now. I don't know what's going on or how to fix it!

[http://paste.ubuntu.com/1002267/](http://paste.ubuntu.com/1002267/)


12.04, no hardware/software raid

---

### Post by Sparticuz on 2012-05-23
So the problem wasn't with grub, somehow my /boot directory got fubar'd and there wasn't actually any kernel in it. Following the directions (loosely) here: [http://askubuntu.com/questions/117027/cannot-recover-grub-due-to-missing-vmlinuz-and-intrd-img](http://askubuntu.com/questions/117027/cannot-recover-grub-due-to-missing-vmlinuz-and-intrd-img)

I was able to reinstall my kernel and boot into my system!

---

