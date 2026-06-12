---
title: "Rsync fills up hdd"
date: 2015-01-29
forum: Server Platforms
---

### Post by mmimaa on 2015-01-29
Hello there,

As the title says I am having some problems with rsync. First of all I should explain my setup. I have the server running from a flash drive (USB 3.0) until I can afford to buy a small hhd, and two 2 TB hdds in RAID 1. Every four hours it's set to do "hourly" backups of the system (~5GB) from the flash drive to the raid array and for the last two days every time it starts the CPU gets to 100% and stays there, thus increasing the temperature by about 15 degrees, and it also fills up my hdds. After the hdd is full, the system probably remounts itself to readonly because I don't have access to any commands saying something along the lines "Unable to open ... Read only filesystem", forcing me to restart the server by holding down the power button.

The first time it did that, two days ago, I found that the file "/usr/.../ubuntu-3.13.0-36-generic/include/config/rt2800pci.h" (not the exact path, since I can't remember where it was) reported an enormous size and it tried to copy until it filled my remaining 1.1TB. I deleted the source and the backup file and I though I solved the problem. Until today when it did it again, but with a twist. The file on the server which reported an enormous size is not the same with the one that is filling my hdd. 

I have attached some screenshots from cacti and ncdu to show its behavior and the latest set of files. On the graphs you can see that somewhere around 19:45, a few minutes earlier than it was scheduled, rsync started and brought my system to a lockdown, forcing me to shut it down. After a few hours I booted it up to look into it and found nothing wrong so I went to sleep. Then at 00:00 another hourly backup started and it filled my hdd.

Screenshots here since the forum only allows me to post 5 at once. [https://imgur.com/a/KhpNN](https://imgur.com/a/KhpNN)

Sorry for the wall of text but since I am still a newbie I am struggling even with troubleshooting the problems and I thought that maybe I could find some help here.

EDIT: I tried to boot it up and it's saying "General error mounting filesystems. A maintenance shell will now be started. CONTROL-D will terminate this shell and reboot the system".
EDIT 2: Since I have access to the shell I am trying now to restore a backup from the beginning of the week. Will update with the results.
EDIT 3: The problems persisted even in recovery mode, so I reinstalled the OS, therefore the problem is gone for now, and hopefully for good.

---

