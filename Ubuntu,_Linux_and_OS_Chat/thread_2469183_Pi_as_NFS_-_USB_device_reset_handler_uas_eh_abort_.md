---
title: "Pi as NFS - USB device_reset_handler uas_eh_abort_handler errors"
date: 2021-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by penguinpages2 on 2021-11-22
Distributor ID: Ubuntu
Description:    Ubuntu 21.04
Release:        21.04
Codename:       hirsute
Linux hypnos 5.11.0-1022-raspi #24-Ubuntu SMP PREEMPT Fri Nov 12 14:11:51 UTC 2021 aarch64 aarch64 aarch64 GNU/Linux
Hardware: CanaKit Raspberry Pi 4 8GB Starter Kit - 8GB RAM,  2TB SSD attached USB3 port

##  Issue:  I had for years used my router to share my backup drive, but with update on their firmware they dropped this feature.. ... working on restoring that or moving to WRT... but ...that is a different story.  Trying to use this Pi, to host NFS share 

Had issues with system hanging when drive query, or various commands to scan drive etc..
Source drive was NTFS format, but to rule that out I tried to wipe it and re-format something more Linux native. EXT4

But still keep getting shell hangs 20-30 seconds, and output in syslog:

Nov 22 08:12:13 hypnos kernel: [ 1627.137056] sd 0:0:0:0: [sda] tag#20 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD IN
Nov 22 08:12:13 hypnos kernel: [ 1627.137089] sd 0:0:0:0: [sda] tag#20 CDB: Read(10) 28 00 e8 e0 7f 88 00 00 68 00
Nov 22 08:12:13 hypnos kernel: [ 1627.153062] scsi host0: uas_eh_device_reset_handler start
Nov 22 08:12:13 hypnos kernel: [ 1627.281944] usb 2-1: reset SuperSpeed Gen 1 USB device number 2 using xhci_hcd
Nov 22 08:12:13 hypnos kernel: [ 1627.306882] scsi host0: uas_eh_device_reset_handler success
Nov 22 08:16:36 hypnos systemd[1]: Started Session 4 of user ansible.
Nov 22 08:16:51 hypnos kernel: [ 1905.668911] sd 0:0:0:0: [sda] tag#18 uas_eh_abort_handler 0 uas-tag 3 inflight: CMD IN
Nov 22 08:16:51 hypnos kernel: [ 1905.668944] sd 0:0:0:0: [sda] tag#18 CDB: Read(10) 28 00 e8 e0 7f 88 00 00 68 00
Nov 22 08:16:51 hypnos kernel: [ 1905.688920] scsi host0: uas_eh_device_reset_handler start
Nov 22 08:16:51 hypnos kernel: [ 1905.817775] usb 2-1: reset SuperSpeed Gen 1 USB device number 2 using xhci_hcd
Nov 22 08:16:51 hypnos kernel: [ 1905.842542] scsi host0: uas_eh_device_reset_handler success
Nov 22 08:17:01 hypnos CRON[2162]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)


Its like the USB kernel driver can't negotiate if it is USB 1 or 2 in connection and speed.   I googled around and various hits but nothing very helpful.

Question:
1) In ubuntu, is their a tool to do a more deep output and debug on drive.... or USB bridge to drive?

Anyone run into this kind of thing such that maybe my use of Pi for basic backup target, is maybe DOA.  My issue is that it is the only other system outside my cluster (well.. besides my $500 router which is being a PITA).. to use for this kind of task.

Thanks

---

### Post by penguinpages2 on 2021-11-30
Just to answer my own post as I found this article:

PiSteps to fix SSD over USB performance issues [https://forums.raspberrypi.com/viewtopic.php?t=245931](https://forums.raspberrypi.com/viewtopic.php?t=245931)

I tried those steps.  It helped some of the issues but then ran into others related to mounting and fsck on boot etc... I have moved on and just conceded that I need to purchase a dedicated NAS.

---

