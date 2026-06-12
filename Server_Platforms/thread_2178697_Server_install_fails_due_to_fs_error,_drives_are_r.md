---
title: "Server install fails due to fs error, drives are reporting healthy"
date: 2013-10-04
forum: Server Platforms
---

### Post by Scrumps on 2013-10-04
Hello, I need some help installing Ubuntu Server on a UEFI motherboard, I am installing the 12.04.3 LTS on a Gigabyte 990FX UD3 AMD motherboard. Everytime I use the installer disc, I can get past the the partition management utility, but it seems to fail at "Installing the Base System". This fails at "The debootstrap program exited with an error (return value 1). Check /var/log/syslog or see vitual console 4 for the details"
When I switch over to that screen, I see three lines that are ext4-fs errors'

For device sda2 which would be the / mount point, as sda1 iis the /boot mount point

"EXT4-fs error (device sda2) in ext4_reserve_inode_write:4688: Journal has aborted
"EXT4-fs error (device sda2) in ext4_evict_inode:243: Journal has aborted

This is the hard drive layout
So I was wondering if anyone could help me out with the install. I am not sure why it keeps failing here. 
sda is 
2 x 80 GB Hard Drives in RAID 1 on Dell Perc 5/i
sda1  UEFIBoot
sda2 /

sdb is
1 x 250 GB Sata Hard Drive plugged into motherboard
sdb1 /home

So far I have not been able to get past this, so any installation help would be appreciated.

---

