---
title: "Deleted Partion and grub is now a black console..."
date: 2016-02-24
forum: Ubuntu/Debian BASED
---

### Post by Aberts10 on 2016-02-24
[ATTACH=CONFIG]267471[/ATTACH]


I am using Zorin OS 11  Based off of Ubuntu 15.10.... Last weekend i setup a dual boot, i created a 50 GB partion by splitting it from my Main OS Windows 10, and i installed Zorin.... Yesterday i got a notice i was low on space, so i booted into windows, Deleted the 50 GB partion and recreated a 500 GB one... After i reinstalled Zorin in the 500 GB partion... i rebooted and found a Black Grub Console.... I've already tried the Bootrec /mbrfix commands and they said they carried out successfully with no advail... I have attached a picture of my partitions.

The solution for me was to download a administrative tool called BCD for Windows/Linux (which I found while browsing a post similar to mine)... I selected automatic repair and it fixed it for me... To reinstall the partition i used the tool mentioned here: [http://askubuntu.com/questions/436096/uefi-and-reserved-bios-boot-area](http://askubuntu.com/questions/436096/uefi-and-reserved-bios-boot-area) and i no longer am having any issues.

---

### Post by howefield on 2016-02-24
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

