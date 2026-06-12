---
title: "SSD install problem Galago UltraPro"
date: 2013-08-22
forum: System76 Support
---

### Post by pj2 on 2013-08-22
I'm having an issue installing windows 8 as a dual boot with Ubuntu on my Galago UtraPro. 

First I swapped out the 500gig hard drive for a Samsung 840 Pro I had prepurchased and installed that, it was picked up in bios perfectly fine. 

Following the system76 guide for setting up a dual boot, installation goes fine until it restarts to complete the windows 8 install process, then it gives a an error stating "Disc read error".
 
Tested the SSD in a different system and it worked perfectly, even once finishing off the install initially started by the Galago. 

Tried using both windows 8 and windows 7, same issue, on first restart after install it gives the same disc read error.

However I was able to install Windows 8 on the original 500gb hard drive the system came with by default and it all works fine.

I'm rather confused as the Samsung 840 Pro is an actual option for hardware when designing your own system.

---

### Post by hawkmage on 2013-08-22
Have taken a look at this page: [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

System76 systems ship with drives that are partitioned with GPT partitions and have BIOS not UEFI.  Win 7 & 8 require a UEFI boot loader with GPT Unless you change the partition type from GPT to MBR.

---

### Post by pj2 on 2013-08-22
I followed the guide for Dual Booting which has a somewhat similar setup. Both involve erasing the drive completely and formatting within the windows setup. This says it should wipe the GPT off it. 
Considering it worked with the HDD it came with which had Ubuntu already installed and after wiping off Ubuntu completely Windows 8 installed perfectly.

I mean I installed a completely new drive that has not had Ubuntu on it and began with Win 8.

Unless theres something else I'm not understanding?

---

