---
title: "Check S.M.A.R.T. on software-ARRAY and get hdd by uuid (for smartctl)"
date: 2012-05-28
forum: Server Platforms
---

### Post by Cyber1000 on 2012-05-28
Hi, I just wanted to activate SMART on my little headless server (Ubuntu 12.04 LTS).

[LIST=1]
[*]Most time the harddrives on /dev/sdx don't change, but it could be, so I would like to access them by id.
In smartd.conf: /dev/disk/by-uuid/uuid-of-a-partion-on-the-hdd [my options]
This works just fine on "normal" disks, but not for disks used in a mdadm-raid, cause they aren't seen by uuid. 
Is there another way to describe disks in a raid-array instead of using /dev/sda or /dev/sdb?
[*]"Normal" smart reads don't bother me, cause it's only collecting online data from the drives. 
A selftest on a "normal" drive doesn't bother me either. But I have some fears running selftests (at least long tests) on drives which make up my RAID 1. 
Should I run them at the same time on both disks, different times, could they disturb normal operation of my md0 array or even make my RAID fail (cause they slow down the disk which is beeing tested?), should I avoid SMART-tests (short, long, both) on RAID-disks at all? 
 
Perhaps someone has more experience on this issue than me.
[/LIST]Thanks

---

### Post by Cyber1000 on 2012-05-28
**Problem partially solved (question 1):**
Ok seems I could go with /dev/disk/by-id/wwn-[unique world-wide-name], as this should always map to the same drives on every reboot and as far as I've read a wwn should even work in another system. And the best: it maps to drives and not only partitions, so I might use this in other szenarios as well ...
 
**Still open (question 2):**
But I still feel uncomfortable with running long tests on mdadm-devices, should I :-)?
 
Thanks

---

### Post by rubylaser on 2012-05-28
Here's how I manage mine with mdadm.  I've never found the need for UUID because the report will include the serial # from the drive.

[http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing]("http://zackreed.me/articles/45-how-do-i-know-if-my-hard-drive-is-failing")
and I set my server up with SSMTP to send the system emails via my Gmail account.
[http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp]("http://zackreed.me/articles/39-send-system-email-with-gmail-and-ssmtp")

I always run long tests on my devices.  If you can't trust them to complete a long test successfully, I'm not sure why you'd trust your important data to them :)

---

### Post by Cyber1000 on 2012-05-28
Hi,
[LIST=1]
[*]I'll use the id, cause /dev/sda is probably not /dev/sda on he next boot and I don't want to test on everything (there is at least one usb-stick around). So I will just enter /dev/disk/by-id/[id] -a W ... -m root for every disk I'll check. Ok that's not the problem anymore :-)
[*]I'm using a postfix-setup, all my "events" like a power shortage on my UPS or something like this is send to my mail.
[*]I trust my important data to them, but I wasn't quite sure how mdadm will handle this, if I access the underlying disks directly (not trough md0). I was only asking if these processes could somehow disturb each other ... . Ok looks like it's ok, then I'll give it a try :-)
[/LIST]thanks for the answer!

---

