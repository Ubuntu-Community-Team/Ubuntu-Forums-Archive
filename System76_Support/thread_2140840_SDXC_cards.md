---
title: "SDXC cards"
date: 2013-04-30
forum: System76 Support
---

### Post by Leslie Dorner on 2013-04-30
I have a current generation System76 Lemur Ultra (lemu4). I have a KomputerBay 128 GB 400X Class 10 UHS-1 SDXC card which is formatted to Microsoft Windows NTFS file system. When I put it into my SD card slot, it automatically mounts the volume correctly, but adding several gigabytes of new data to the SDXC card results in input/output errors. I tried to format it to /ext4 files system using GParted or Disks and it never seems to be able to write the new /ext4 file system correctly hence I can't mount it as an /ext4 volume. I tried to combine /ext4 file system with LUKS encryption and it creates the LUKS volume correctly, but it never successfully writes the /ext4 file system. Hence, it fails to mount the /ext4 file system after I enter my LUKS password with an error stating that no file system was found with the LUKS encryption partition.

I checked the latest System76 3.2.7 device driver and there's no mention of anything regarding the SD card reader for the lemu4 and Ubuntu 13.04 64 bit Raring Ringtail. I've been told the SD card reader device driver was committed upstream.

How can I get this to work properly? I just want to use it as a regular data drive. I would prefer to format it to /ext4 with LUKS combined. How do I get that to work properly?

Please help if you can. Thank you.

PS:

I tried a PNY 128 GB 233X Class 10 UHS-1 SDXC card and it got destroyed twice which required me to request two RMAs from PNY Technologies, Inc. So, scratch PNY SDXC cards with the lemu4.

---

### Post by Leslie Dorner on 2013-04-30
I just upgraded to Linux kernel 3.9 64 bit for Ubuntu 13.04 64 bit. Is this going to help to solve my problem with 128 GB SDXC cards?

---

### Post by Leslie Dorner on 2013-04-30
It still does not work. I got an Anker USB 3.0 SDXC card adapter and it won't format to /ext4, NTFS, or enable LUKS encryption.

---

### Post by isantop on 2013-05-01
More than likely, upgrading to a new kernel that isn't coming from Ubuntu won't fix any problem,s and has a tendency to introduce new problems. I'd uninstall that kernel, as it will cause instability in other areas of the system.

---

### Post by gordintoronto on 2013-05-01
Do you run Gparted by opening a terminal and typing this command:
sudo gparted

then select the card?

Are you sure the SD card slot supports a 128 GB card?

---

### Post by isantop on 2013-05-01
Our card readers don't support 128 GB SDXC cards with LUKS encryption. Going with a 64 GB card is better.

---

### Post by Leslie Dorner on 2013-05-01
Now you tell me after I bought it. I gave it to my father. He's got a brand new Lenovo IdeaPad z400 notebook PC with Microsoft Windows 8 64 bit Home. It is fully compatible with the KomputerBay 128 GB 400X Class 10 UHS-1 SDXC card.

I am thinking about getting this KomputerBay 64 GB 600X Class 10 UHS-1 SDXC card:

1. [http://www.amazon.com/gp/product/B004LCIU1E/ref=twister_B005793ZTW?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B004LCIU1E/ref=twister_B005793ZTW?ie=UTF8&psc=1)

Now, before I buy it from Amazon, please tell me if this is compatible or not. I plan to format it to use /ext4 file system and LUKS encryption. Is it going to work or not?

---

### Post by isantop on 2013-05-02
We've heard good results regarding 64 GB card, but on the other hand, SD cards don't seem to like encryption enyway. If you need encryption, going with a Flash drive is a much better option, as they're much more durable and known to work well with encryption.

---

### Post by Leslie Dorner on 2013-05-02
Thank you. I decided against geting it after your reply.

---

### Post by Leslie Dorner on 2013-05-03
I downgraded from Linux kernel 3.9.0 64 bit to 3.8.0-19-generic for Ubuntu 13.04 64 bit today. All is good with my System76 Lemur (lemu4). I'm thinking that Linux kernel 3.9.x.y will be included with Ubuntu 13.10 64 bit if not 3.10 64 bit. That would be good news for cryptography experts like myself.

---

### Post by isantop on 2013-05-06
We should be seeing at least 3.9 in 13.10. It could very well be higher than that by two or three versions.

---

