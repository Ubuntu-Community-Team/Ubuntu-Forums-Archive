---
title: "Boot fails due to degraded RAID"
date: 2012-01-12
forum: Server Platforms
---

### Post by DooMMeeR on 2012-01-12
I have set up a new Ubuntu 11.10 installation an a machine
the machine contains a RAID but the system is installed to a single ext4 partition on a seperate drive

the machine ran a 10.04 installation before and would boot just fine even if the RAID could not be assembled

now the boot fails with mdadm complaining about a degraded RAID and jumps to a initramfs emergency shell

whenever I disconnect the disks which are part of the RAID the boot completes just fine

why?

the RAID is not even mounted during init nor is it listed in fstab

10.04 would simply assemble the RAID with all disks marked as SPARE and thusly have the RAID inactive after boot
that was a by far better solution than it is now, because the machine would not boot anymore of the raid is desynced due to a powerloss or any other nonfatal issue

---

### Post by rubylaser on 2012-01-12
Is there a reason you left the 10.04 the LTS to move to the newer 11.10 (hardware, older packages, etc)?  Otherwise, I've always stuck with LTS releases on my servers.  If it's working, don't fix it :)

That aside, have you set your array up to boot degraded, and installed grub on the second hard disk?  
[https://help.ubuntu.com/community/Installation/SoftwareRAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID")

---

### Post by CharlesA on 2012-01-12
You might have to add "nobootwait" to fstab to get it to boot if the array is degraded. I'm assuming you have the array set to mount on boot, but if you don't than that won't work for you.

I run into a similar problem after kernel updates since I need to rebuild the drivers for my RAID card and the array isn't seen by the OS until that is done.

EDIT: Nevermind, different problem. Check out the link ruby posted.

---

