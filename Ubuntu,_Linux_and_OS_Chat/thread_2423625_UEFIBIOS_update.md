---
title: "UEFI/BIOS update"
date: 2019-07-26
forum: Ubuntu, Linux and OS Chat
---

### Post by shygorgon on 2019-07-26
Hello everyone,

I have been using linux for a while now (mainly Ubuntu), and have 2 questions. My first question is about updating the UEFI/BIOS on my laptop. The laptop I am running now is a Sager (Clevo) 9377 that I purchased new back in early 2015. It is still running great, and I have not had any problems, but I am trying to do some research into updating the UEFI/BIOS. I have not updated it since I got the laptop, and I figure it is about time to do so, and I was looking for a straightforward and (if possible) easy way to do this. I was hoping to find a UEFI/BIOS that was specific to linux in general. My second question is on how (and if) to install Banshee on my system. I noticed that Banshee is no longer available in the software center, and IO have not been able to find a .deb file to download and install from. Are there any recommendations to do this?

Here are my system specs to make it easier for help:

Sager 9377 (Clevo 9377 motherboard)
Ubuntu Studio 19.04 (64-bit)
Intel Core i7 3.1GhZ CPU
Dual nVidia GTX 980M (8GB) GPUs
32 GB Kingston Tam @1600 Mhz
2x1TB Samsung Evo 840 SSDs
Bluray/DVDRW/CDRW optical drive

Thanks for any and all help.

---

### Post by oldfred on 2019-07-26
What does your manual say?

Some now directly update from Linux.
       [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) 
    
Both my Asus & Gigabyte based desktops will update from inside UEFI reading the update file from a FAT32 partition. I download into my ESP - efi system partition or a separate USB flash drive.

My 18.04 shows Banshee is available.

---

### Post by uRock on 2019-07-26
19.04 doesn't have Banshee. That said, there's a PPA for it.

```
sudo add-apt-repository ppa:banshee-team/ppa
sudo apt update
sudo apt install banshee
```

---

