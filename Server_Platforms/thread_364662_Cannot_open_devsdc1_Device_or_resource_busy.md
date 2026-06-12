---
title: "Cannot open /dev/sdc1: Device or resource busy"
date: 2007-02-18
forum: Server Platforms
---

### Post by unixpaul on 2007-02-18
Hello,
I'm just installed Ubuntu Dapper 6.06. It has 4 SATA drives. The system is installed on the first, sda1. I have created partiions on /dev/sdc and /dev/sdd  for software RAID, however
it keeps telling me they are in use. 

mdadm --create --verbose --auto /dev/md1 --level=1 --raid-devices=2 /dev/sdc1 /dev/sdd1
mdadm: Cannot open /dev/sdc1: Device or resource busy

But they are clearly not. They are not listed in when I issue a 'mount' command to show whats mounted. Also 'fuser'  shows no files with /dev/sdc or /dev/sdd in use.
What has claimed by disks, and how do I get them back?

Paul

---

### Post by Macchi on 2007-02-18
Hello unixpaul,

Have you tried to create the RAID partitions and configure the software RAID through the Ubuntu installer?  Why are you building it manually? The alternate install allows you to do that and my experience is that it always worked out of the box when correctly configured. I have even used more complex configurations with LVM on RAID and obtained success without any difficulties. 

I believe that I read something about issues with SATA drives on older kernels, but it is my impression that those problems have been solved.

PS: Remember to use distinct names for the LVM components, otherwise recovery may be difficult in case of problems. I read that on an article in the Linux Journal.

---

### Post by pgjensen on 2008-06-24
ever figure this out?  doing it for me, too.

i can make partitions on devices and write to them using dd... but can't mkfs on them or make raid :(

---

