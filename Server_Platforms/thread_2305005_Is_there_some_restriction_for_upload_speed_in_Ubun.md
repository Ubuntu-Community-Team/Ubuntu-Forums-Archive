---
title: "Is there some restriction for upload speed in Ubuntu server ?"
date: 2015-12-02
forum: Server Platforms
---

### Post by soamz on 2015-12-02
Hi, I have Plex Media Server installed at a server. 
Server is connect to the router with its own static IP and I connected wired to the same router as well with my own static IP.
So, basically both are on the same router switch. 

Now when I upload the movie files, it says, "the upload speed is not going over 1.3MB/sec".

Why is that restrict ?

LAN should go around 100MB/sec or even 200MB/sec since its gigabit to gigabit card transfer. 

Im using WINSCP for the upload. 

What am I missing ?

---

### Post by MAFoElffen on 2015-12-02
While your actual rates are low... On a single segment gigabit network, after you translate from Gb to GB, the theoretical max is 125MB/s. After you figure in your bus, the number of drives, how your drive controller is connected to your bus, the number of drives, the types of drives drives and where the data is on those drives... On a 1.5Gb transfer rated SATA, your transfer rate if the data is at the edge of the drive on a sustained transfer is down at 35MB/s. Then processors, RAM and cabling are also a factor.

For example a sustained write to a software RAID1 is writing the same data to 2 drives, through a bus where other resources are being allocated... Where the CPU is processing the software RAID, memory buffers for the transfer, etc...

So while I run dual 16 core cpu boxes with 265GB RAM, 10k 6Gb/s eSATA's on 6Gb/s Hardware RAID PCIE Controllers, using RAID6 and have a fiber channel backbone between my servers, I still have to wait for GB's of Data to transfer from one server to another. Having said that, there "are" a lot of factors to look at to find where you might be loosing bandwith. And yes, 1.3MB/s seems a bit low over a single segment home network with no other competing traffic. Maybe assess what you have, measure the load... then tweak your IPv4 and TCP settings in sysctl.

---

### Post by soamz on 2015-12-02
WINSCP was crazy slow around 1.3MB/sec

Did it with FileZilla and it happened at 67MB/sec .

---

### Post by mastablasta on 2015-12-02
> **soamz said:**
> WINSCP was crazy slow around 1.3MB/sec

Did it with FileZilla and it happened at 67MB/sec .

perhaps you missed a setting in WinSCP or used a different protocol on transfer.

---

### Post by SeventhGear on 2015-12-02
> **MAFoElffen said:**
> Maybe assess what you have, measure the load... then tweak your IPv4 and TCP settings in sysctl.

I am running into similar issues with my home network. Do you know which settings I would need to tweak? Or if you have a link to something that I could read about the settings would be fine.

---

