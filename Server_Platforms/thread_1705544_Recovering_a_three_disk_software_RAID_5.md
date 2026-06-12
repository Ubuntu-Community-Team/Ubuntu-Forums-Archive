---
title: "Recovering a three disk software RAID 5"
date: 2011-03-12
forum: Server Platforms
---

### Post by ttist25 on 2011-03-12
Hello there.  

I'm testing my ability to recover a failed disk on a three disk software RAID 5 setup.

I have used a 10.04 alternate install disk to setup a three disk RAID 5 array according to this: [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html).  This is for a RAID1 setup.  I followed it exactly except that I performed the steps on three drives rather than two and selected RAID5 instead of RAID1.  Each disk is 500GB and has a 26 GB swap partition and the remaining space on each disk set as / with the boot flag on.

I installed the OS on my array and everything boots without a problem.  After I booted up I started a terminal and ran**sudo dpkg-reconfigure mdadm** to set the boot degraded to true and rebooted.  

Next, I shut down the computer, disconnected the power on drive 1 (sdb) and then tried to boot.  I get this (not verbatim):

> 
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
raid5: raid level 5 set md0 active with 2 out of 3 devices, algorithm 2
mdadm: /dev/md0 has been started with 2 drives (out of 3)
raid5: failed to run raid set md1
mdadm: failed to RUN-ARRAY /dev/md1: Input.output error
mdadm: Not enough devices to start the array while not clean - consider --force
Started the RAID in degraded mode
Gave up waiting for root device:


*then a list of common problems and then:

ALERT! /dev/disk/by-uuid/bunchanumbersnad letters does not exist.  Dropping to a shell
Then it dumps me to initramfs.  MD0 is the swap partition.  At this point I don't know what the heck to do.  I'm skating on the edge of noobidity and this is pretty much over my head.  

I want to use this server as a virtual machine server and the desired behavior would be that, if a hard drive should fail, the server would alert me via email and continue to run in a degraded state.  

Is it even possible to install the OS on the array and run it degraded?  Given the desired behavior, should I be looking at something other than RAID5?  My client is broke so I'm trying to avoid a hardware RAID if I can do it.  

Thanks in advance for any help you can provide.  It will be GREATLY APPRECIATED.  I've been at this for three days and I'm growing weary!  :)

---

### Post by YesWeCan on 2011-03-13
Hi there and welcome to the forum. I see you posted this 1 day ago; normally you would get a response much sooner.

One possibility is that Ubuntu is refusing to boot a degraded RAID array. It defaults to this as a sort of safety measure because sometimes booting from a failed array can damage the array further. So you should try adding the "bootdegraded=true" kernel option to the Grub2 bootloader kernel commands.

You need to enter the Grub2 menu when you boot and then edit the correct boot command line. See [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and scroll down to the heading "Editing Menus During Boot". The line you want to add to is the one ending in "ro quiet splash" so it looks like "ro quiet splash bootdegraded=true".

Have a go and see if that works. :)

> Is it even possible to install the OS on the array and run it degraded? Given the desired behavior, should I be looking at something other than RAID5? My client is broke so I'm trying to avoid a hardware RAID if I can do it.
Yes. This is not a limitation of RAID 5 per se.

---

