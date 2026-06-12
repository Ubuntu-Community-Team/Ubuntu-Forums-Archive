---
title: "How I muffed my 8.10 install"
date: 2008-10-30
forum: Testimonials &amp; Experiences
---

### Post by paul42 on 2008-10-30
Short version: Did not format the /boot partition on install, Grub was not updated, and it kept trying to boot from an older kernel that was not on my system. No mouse or keyboard in GDM, and no network.

Having a dual boot between 7.10 & Vista, I'm always a little cautious when it comes to the partitioning part of the install.  Getting to that point, I had three options;

1) Default - resize the existing ext3 partition, and use that for ubuntu.
2) Wipe the entire drive
3) "manual"

As I wanted to keep Vista for games, door 3 seemed my only option.  I chose that and left the ntfs and swap partitions as they were.  I set the mount point for /boot and /, and then carried on my merry way with the install.  Everything seemed okay until I rebooted into GDM, and had no mouse or keyboard.  Ctrl-Alt-F2 worked though, and I was able to login to the console, where I saw that I had no network.  Checking syslog, I could see that the system was looking for an older kernel that did not exist, hence a re-install with formats applied to both partitions I was installing on.

---

