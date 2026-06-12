---
title: "Partitioning for another OS problem."
date: 2007-11-28
forum: System76 Support
---

### Post by mpow on 2007-11-28
Hi, I have a serp3 lappie and I want to add Windows because I want to play some games and it's $5 at my university, I found Sys76's guide to partitioning and my file system doesn't look the same in GParted. I am worried about partitioning my hard drive because GParted doesn't look like it recognizes 74.31 Gigs as any partition type. In the attached screen shot, it shows my GParted screen. (The screen shot is taken from using the Ubuntu 7.10 Live CD)
On a related note, would it be possible to install windows onto a portable hard drive? I have a 500 GB one that I wouldn't mind using. 

Thanks in advance,
Martin

---

### Post by thomasaaron on 2007-11-28
Your computer has lvm partitioning. You can't re-size it to install Windows.
If you want to dual boot Windows, you will need to re-image your machine and use non-lvm partitioning.

The best way to do that would be to install Windows first and allow it however much hard drive space you want. Then install Ubuntu in the remaining space. It will automatically detect Windows and create a grub menu for you.

Your other option would be to virtualize Windows using vmware. Then you won't have to mess with your current installation. You can download vmware server from the repositories (Application > Add/Remove).

---

