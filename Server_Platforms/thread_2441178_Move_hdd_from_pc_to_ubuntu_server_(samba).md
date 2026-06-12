---
title: "Move hdd from pc to ubuntu server (samba)"
date: 2020-04-20
forum: Server Platforms
---

### Post by olsonkp48 on 2020-04-20
Warning Old Noobie!
For fun and stimulation, I have decided to build an Ubuntu server for my home network. 
I have old parts from previous computer builds, so the physical build part won’t be a problem. (Always add “I hope” to the end of every sentence.) New case and power supply, old mobo and processor, 256 GB SSD. 

I will have questions about partitioning the SSD for the server software, since the SSD is “so big.” (How many, how big, etc.)

So can I move my physical HDD to the server? For example, one of my HDD has only photos on it, so to make it easier access on the network, I would love to simply move it to the server box.

Would it be as simple as it sounds?

The server would be Ubuntu Server LTS 20.04 (I think), and the Samba role. (Do I have that right?)

This old dog wants to learn some new tricks. But don’t make the answers too complex (yet).
Thanks,

Ken
olsonkp48

---

### Post by slickymaster on 2020-04-20
*Thread moved to **Server Platforms**.*

---

### Post by Tadaen_Sylvermane on 2020-04-20
Linux systems can usually mount Windows NTFS partitions without to much trouble. That being said, even if you do use samba I'd try to find a way to backup that drive then change to a Linux standard format, ext4 or something. Not requiredof course but a good idea at some point if you intend to stay with the Linux side of things for a server.

As far as partitioning I'd keep it simple. 25gb for root volume, 2gb for a swap volume. Keep the rest unoccupied for eventual as needed expansion of root volume. May want to put /var on it's own volume as well. I've heard of occasional logs getting away from the system and taking over the drive. Linux kind of chokes when it has no free space on the root partition.

---

