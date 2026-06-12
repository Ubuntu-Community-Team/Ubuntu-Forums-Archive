---
title: "New Partition advice"
date: 2015-06-28
forum: Ubuntu, Linux and OS Chat
---

### Post by manderman85 on 2015-06-28
Alright so I'm new for the most part to Ubuntu and I was just about to set up a partition using minitools. I currently have 2 HDD in my pc and I was planning using the 2nd  so I would still have my windows 8.1 there on the main but i'm not sure which file system to use, which version of Ubuntu (14 or 15) and what size I should make it. When I first tried to instill Ubuntu 14 I tried to make a new partition I was getting "No root file system defined" error. I do want to keep it on a different HDD for sure.

---

### Post by Bashing-om on 2015-06-28
manderman85; Hi ! Welcome to the forum.

As A new user of linux in general and 'buntu in particular, may I point out to keep it simple starting out.

It gets no simpler than to disconnect the drive that contains Windows, boot the ubuntu installer and choose the option " erase disk and install ubuntu" .

Over and one with in a matter of minutes. At some later stage in your learning experience it is a very small matter to save your data , then partition the hard drive to suite your known use-case.

This thought is open to debate and discussion . It is your system, we do it your way.

[INDENT][INDENT][INDENT]I do promte the 
[INDENT][INDENT][INDENT]KISS principle 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-06-28
If Windows 8 was pre-installed then it is UEFI. Just be sure to boot Ubuntu installer in UEFI boot mode, so it installs in UEFI boot mode also. 
If you manually installed Windows 8 in BIOS mode, then you want to install Ubuntu in BIOS boot mode.
But both systems need to be in same boot mode.

For a new user Bashing-om's suggestion is good.
If you want detailed instruction for the Something Else install option. You do have to select which partition you want for / (root), what format (ext4) and tick format box. Same for swap but it has not format.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by rewyllys on 2015-06-29
> **oldfred said:**
> . . . . You do have to select which partition you want for / (root), what format (ext4) and tick format box. Same for swap but it has not\ format. . . .
I strongly urge you to create (during the install procedure -- or before it using Gparted) a separate partition for your /home directory.  Thus you will have 3 partitions on your second HDD: / (i.e., your root directory), /home (i.e., your home directory), and /swap.

This will greatly simplify later updating of your installation.

---

### Post by oldfred on 2015-06-29
+1 on rewyllys suggestion

New users just using a small amount of space are fine with the default install of / & swap. But that same default was the standard when Ubuntu first started and a large hard drive was 100GB or even less. Now with larger hard drives splitting / & /home make sense for newer users or those that know they want and will keep Ubuntu.

But I actually use a slightly more advanced configuration with data partitions. My / is 25GB including /home, but all data is in my data partitions. I started using a data partition when dual booting with XP many years ago. Then I had two data partitions, one NTFS for any data I might share with Window and a Linux format for data I only wanted to share with Linux installs.

---

