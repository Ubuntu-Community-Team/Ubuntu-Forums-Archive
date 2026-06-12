---
title: "Ubuntu 10.04 Raid on HP Proliant ML115"
date: 2010-05-17
forum: Server Platforms
---

### Post by X1R1 on 2010-05-17
I have a problem installing Ubuntu on an HP Proliant ML115. This server has a 1TB mirrored RAID setup (and 1 250GB drive), problem is, Ubuntu apparently doesnt like it, it detects the RAID but fails to partition the hard drives and the installation cant continue. I tried the guided partitioning using the whole disk (detected RAID array).

Here is what syslog gives me:

May 17 22:32:30 main-menu[504]: INFO: Menu item 'disk-detect' selected
May 17 22:32:30 net/hw-detect.hotplug: Detected hotpluggable network interface eth0
May 17 22:32:30 net/hw-detect.hotplug: Detected hotpluggable network interface lo

May 17 22:32:31 hw-detect: Loading PCMCIA bridge driver module: i82365
May 17 22:32:31 hw-detect: FATAL: Module i82365 not found.
May 17 22:32:32 check-missing-firmware: no missing firmware in /tmp/missing-firmware

May 17 22:32:32 anna-install: Installing dmraid-udeb
May 17 22:32:32 disk-detect: Serial ATA RAID disk(s) detected.
May 17 22:32:35 disk-detect: Enabling dmraid support.
May 17 22:32:35 dmraid-activate: ERROR: Cannot retrieve RAID set information for nvidia_eifaaiia

May 17 22:32:35 dmraid-activate: ERROR: Cannot retrieve RAID set information for nvidia_eifaaiia
May 17 22:32:36 check-missing-firmware: no missing firmware in /tmp/missing-firmware
May 17 22:32:36 main-menu[504]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)

May 17 22:32:36 main-menu[504]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
May 17 22:32:36 main-menu[504]: INFO: Falling back to the package description for console-setup-udeb
May 17 22:32:36 main-menu[504]: INFO: Falling back to the package description for console-setup-udeb

May 17 22:32:36 main-menu[504]: INFO: Menu item 'partman-base' selected
May 17 22:32:41 partman: Error running 'tune2fs -l /dev/mapper/nvidia_eifaaiia'
May 17 22:33:01 partman-lvm:   Device /dev/mapper/nvidia_eifaaiia5 not found (or ignored by filtering).


Any other info you need just ask, it is very urgent.

PS: Im very noob regarding this kind of stuff so detailed instructions please, also feel free to give configuration tips :D

Regards and thanks for the help.

---

### Post by jbrown96 on 2010-05-17
Is the RAID through the BIOS or a dedicated RAID card? Are you dualbooting this with Windows? When you boot Ubuntu what does ```
sudo fdisk -l
``` report?

---

### Post by X1R1 on 2010-05-18
Boot Through BIOS, I configured it (pretty easy to setup I just needed to select the drives and apply changes).

Regarding the output, I will do it tomorrow and come back (im at home now, server is at work).

thanks in advance

---

### Post by jbrown96 on 2010-05-18
If you are not dualbooting, then configuring the RAID in Linux is much better than through the BIOS. Linux does not have great support for hardware raid (including via BIOS); however, that doesn't mean that your chipset is not supported.

---

### Post by X1R1 on 2010-05-18
So, I should just delete the array and use software RAID for the disks?

yes ubuntu will be the only system on this server.

---

### Post by jbrown96 on 2010-05-18
> **X1R1 said:**
> So, I should just delete the array and use software RAID for the disks?

yes ubuntu will be the only system on this server.

That's my suggestion. If you use hardware raid, then you won't get any warnings if a disk fails. 

The traditional argument against software RAID is that it uses too much of your CPU, but that's simply not true on any multi-core systems. On multi-core, hardware RAID can also be a bottleneck. Furthermore, if you're hardware RAID card goes bad, then you have to get one from the same manufacturer (or in many cases the exact same model and revision); whereas in Linux, software RAID is standardized and you can use any version of Ubuntu or any other Linux distribution with no problems. 

I believe that you will need to use the Alternate disk to install onto a RAID array. You will probably want to read up on the mdadm command, which is used to create, modify, and check RAID volumes.

Using software RAID also gives you finer-grained controls. Let's say that you want to have swap (something that I feel is usually unnecessary), /home, and / spread over three disks. There's no reason for swap to be in a RAID array since the data is extremely temporary. / should probably only be on RAID1 since uptime matters but there is no unique data that cannot be downloaded again or restored from backups. /home, or with a server /var, are probably very important and may need RAID5 (or with four disks RAID6). With hardware RAID, you have to use entire disks and there's no flexibility. However, software RAID allows you to create a good RAID array that gets maximal data integrity for the important parts (/home and /var), reasonable integrity for /, and minimal overhead for swap.

---

### Post by X1R1 on 2010-05-18
jbrown86, thanks a lot for your detailed response, Im elightened!

When you refer that I will need to use the alternate disk to install onto a RAID array, you mean that I should install ubuntu on the 250gb drive and then, from there, configure the other 2 drives (the 1 TB ones) with software RAID?

I can see on the manual partition menu the option to configure software RAID, so im thinking I could just configure and install ubuntu there without using that alternate disk you are refering about.

Also, whats the best RAID to configure? I want complete assurance that my data will be secure in case of failure, max fault tolerance here, so Im guessing RAID 1 could be the solution here, but I want to take an informed desicion :D

regards

---

