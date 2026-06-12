---
title: "Adding raid to pre-existing server install?"
date: 2009-03-17
forum: Server Platforms
---

### Post by supaphly42 on 2009-03-17
So I have a server that I built up using Ubuntu (7.10 I think). At the time, I only had one drive, but have since been able to buy a second. I want to set it up for RAID 1 using software, but don't want to do a fresh install of Ubuntu and lose everything I have. Any ideas/suggestions??? Thanks!

---

### Post by papenpj on 2009-03-17
I found this [Guide]("http://beginlinux.wordpress.com/2008/05/30/raid-lvm-and-acls-on-ubuntu-804/") the other day.

Well it more of a quick review of ubuntu but it mentions several things about setting up a raid and i believe it can be done without a fresh install. If it wasn't so late I would double check the link to see if it is also the one that mentioned when running raid how you also need to set it up for grub on both drives and the issues that can arise. Ill check tomorrow.

EDIT:
I double checked and the guide i posted was not what i orignally intended, it decent but i know i read a better one. I also found 
[Install Raid on existing ubuntu]("http://ascendwiki.cheme.cmu.edu/Installing_Raid_1_on_Existing_Ubuntu_Server") however, im assuming you want to backup the whole filesystem and not just one directory.

---

