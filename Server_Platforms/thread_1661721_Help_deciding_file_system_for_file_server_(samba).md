---
title: "Help deciding file system for file server (samba)"
date: 2011-01-07
forum: Server Platforms
---

### Post by mekitokazi on 2011-01-07
Hey experts!,

I'm planning to add 1tb sata disk to my lovely file-server under ubuntu 10.10,
what i want is use this disk as additional storage for network user,
the question is, what is the best file system for easy use both windows and ubuntu?

I mean when my ubuntu server down (worse case) I can easily take out the disk from ubuntu machine and plug in on windows machine 

is fat32 capable doing so?

Thanks!

---

### Post by disabledaccount on 2011-01-07
File server is supposed to hold data - I can't imagine holding such amount of data without hdd redundancy, even if we are talking about temporary files. In other words: You should be more aware of possible HDD failure - this is far more dangerous.

But, if you belive in your luck then here you have little overview:
- Ext4 is supported under windows (with 3rd party driver)
- FAT32 will work fast on both systems, but it don't support permissions
- NTFS is deadly slow under linux

---

### Post by aceofspades686 on 2011-01-07
FAT32 has a lot of limitations as far as what can be stored on it, which I would not recommend for a file server.  One big limitation is the inability to store a file larger than 4GB.  The only other option for Windows is NTFS (unless someone knows something I don't, then please speak up) but last I knew the linux drivers for NTFS were unable to change NTFS file ownership/rights and it also has issues with filesystem level encryption and compression.

My personal suggestion would be to go with a Linux filesystem you're familiar with (probably ext3 or ext4), then if for some reason you need to plug the drive into another machine, keep an Ubuntu Desktop live cd around so you can get the data from it that way.

EDIT:

> **tomazzi said:**
> File server is supposed to hold data - I can't imagine holding such amount of data without hdd redundancy, even if we are talking about temporary files. In other words: You should be more aware of possible HDD failure - this is far more dangerous.

But, if you belive in your luck then here you have little overview:
- Ext4 is supported under windows (with 3rd party driver)
- FAT32 will work fast on both systems, but it don't support permissions
- NTFS is deadly slow under linux

This, all of it plus the limitations I mentioned.  Its interesting to know that there is a 3rd party ext4 driver for Windows now.

Also, I want to strongly second the mention of HDD redundancy, as well as regular backups to another drive.

---

