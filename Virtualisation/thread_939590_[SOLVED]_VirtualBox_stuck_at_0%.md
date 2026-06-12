---
title: "[SOLVED] VirtualBox stuck at 0%"
date: 2008-10-06
forum: Virtualisation
---

### Post by lian1238 on 2008-10-06
VirtualBox won't load my XP virtual machine. Usually, when I start it, it'll just boot right away. But now, it says "Starting the virtual machine..." and doesn't change from 0%. And it doesn't seem to be using the CPU either.

---

### Post by lian1238 on 2008-10-06
Solved it now. After I rebooted, it was no longer stuck at 0%. There was an error: [B]FATAL: Could not read from the boot medium. System Halted!
[/B]
What I did was go into Settings->Harddisks, then I chose the vdi file of my XP virtual machine. Now it boots normally. :)

---

### Post by run1206 on 2008-10-08
i have the same problem, yet my hard disks are .vmdk files.  is their any way how i might be able to switch them to .vdi files?

edit: nm, my problem was that i didn't have the module vboxdrv installed fully after upgrading to Intrepid.  i installed linux-headers-generic and ran sudo modprobe vboxdrv and it runs great!

---

