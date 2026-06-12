---
title: "converting single disk LVM to RAID1 LVM (grub)"
date: 2010-05-05
forum: Server Platforms
---

### Post by geraldbrandt on 2010-05-05
Hi,

I have an Ubuntu Server on (8.10) running under Citrix XenServer (though that shouldn't make a difference).

I installed on a single disk:

xvda1 - 200 MB - /boot
xvda2 - 9.8 GB - LVM (ubuntu-base)

The LVM is:

swap  - 1.0 GB
root  - 8.8 GB - /

I have successfully gotten this converted to RAID1 by adding a new drive (xvdb) and following the Debian howtoforge article ([http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub-configuration-debian-lenny](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-lvm-system-incl-grub-configuration-debian-lenny)).

What I have not been able to do, is get grub working properly.

If I fail xvdb and reboot the system, everything comes up and I can reboot and run.

If I fail xvda and reboot the system, XenServer gives me a bootloader error.  i.e.: no grub

I have no idea what I'm doing wrong here.  If someone has done this, can they tell me what grub commands to run to get a successful boot of the primary disk fails?

Thanks,
Gerald

---

### Post by Akita on 2010-05-05
You need to run grub and install the bootloader on the 2nd drive also. Grub by default only puts it one the first and knows nothing about software RAID. It's been a while but basically you run grub to get it's interface, tell it to use the 2nd disk and set that up as bootable. The result is that when onde disk goes away, the BIOS will boot the remaining drive and grub will find what it needs there.

---

