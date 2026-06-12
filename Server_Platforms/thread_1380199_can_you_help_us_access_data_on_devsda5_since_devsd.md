---
title: "? can you help us access data on /dev/sda5 since /dev/sda1 (root) boot fails?"
date: 2010-01-13
forum: Server Platforms
---

### Post by mphhpm on 2010-01-13
[U][B]GOAL
[/B][/U]1. access data on /dev/sda5

_**BACKGROUND AND FAILURE**_
* our 6.06.2 has been humming along working fine for over 2 years.
* last night, ftp, ssh, https all failed.
* strangely, http and mysql kept right on running.
* access from the console locked up - forced a hardware reset.
* upon reset boot fail Grub 15.

**_RESOUCES_**
 * we have a nearly identical hardware backup to this system.
 * the difference is only the data stored on /dev/sda5

**_REMEDIES THAT DON'T WORK_**
* opening shell in root partition from rescue mode - fails
- "no usable shell found on your root: /dev/discs/disc0/part1"

* running /target/sbin/grub on root partition (rescue allows shell to install environ) - fails
- "error while loading shared libraries: libncurses.so.5 cannot open shared object file"

* hotplug of hd0 from primary server to open bay on backup server - fails
- the primary hd0 spins up, LEDs on, but /dev not updated to reflect hotplugged device.
? is there a way to force scsi bus to rescan scsi chain to find the hotplugged hdd?

---

### Post by doas777 on 2010-01-13
well if you just need access to teh data, boot off a livecd.

---

### Post by mphhpm on 2010-01-13
> **doas777 said:**
> well if you just need access to teh data, boot off a livecd.
* thank you, doas777
* in my and our shock and awe over the dead server we were not thinking clearly.
* we were able to mount the desired partition on the non-bootable drive.

! and the results were shocking!
* the following dirs are missing (yes gone!): [COLOR=Red]bin,etc,lib,boot,home,root[/COLOR]
* and these dirs are empty: dev, proc

? can anyone comment on how these dirs would disappear on a running server?

---

### Post by HighCommander540 on 2010-01-13
> **mphhpm said:**
> * thank you, doas777
* in my and our shock and awe over the dead server we were not thinking clearly.
* we were able to mount the desired partition on the non-bootable drive.

! and the results were shocking!
* the following dirs are missing (yes gone!): [COLOR=Red]bin,etc,lib,boot,home,root[/COLOR]
* and these dirs are empty: dev, proc

? can anyone comment on how these dirs would disappear on a running server?

Someone hacked you and deleted them. Or hardware got fried. Only two reason.

---

### Post by mphhpm on 2010-01-13
> **HighCommander540 said:**
> Someone hacked you and deleted them. Or hardware got fried. Only two reason.
* i just remembered that this hard drive was nearly full.
* i recall it was about 98% of 73GB.
? could a full hard drive have caused this problem?

---

### Post by HighCommander540 on 2010-01-13
> **mphhpm said:**
> * i just remembered that this hard drive was nearly full.
* i recall it was about 98% of 73GB.
? could a full hard drive have caused this problem?

Well I have never heard of it. It usually just stops writing to the hard drive. It wouldn't get rid of a lot of it.

---

