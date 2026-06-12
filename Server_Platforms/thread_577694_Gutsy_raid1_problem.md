---
title: "Gutsy raid1 problem"
date: 2007-10-16
forum: Server Platforms
---

### Post by Gone fishing on 2007-10-16
I'm having hair pulling out problems setting up Raid1 on gutsy server. I'm following these instructions [http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)  but setting up three Raid partitions one for / one for /home and the other for swap. Everything seems to work the partitions appear in fstab and  cat /proc/mdstat looks OK everything is fine, until I try and remove a hard drive to test the system and try to boot, then the system refuses to boot. 

This looks similar to my problem [http://ubuntuforums.org/showthread.php?t=507074&highlight=raid1](http://ubuntuforums.org/showthread.php?t=507074&highlight=raid1)

will this solution work?

---

