---
title: "Question about jumping from onboard sata to Dedicated Raid Controller"
date: 2013-03-26
forum: Server Platforms
---

### Post by grunge09 on 2013-03-26
I am running 12.10 Ubuntu Server on a Skt 939 mb with an AMD 6000+ CPU, and am using 4 of the 6 sata2 ports on the motherboard.  Running Mdadm RAID5 all 2TB Drives (3 2tb drives in RAID5 with a 2tb Spare).  Booting off a 8gb flash drive and running ok.

I have a CDROM but its on an IDE port so its not an issue.  

I am looking at an inexpensive 8 port PCI-Express RAID controller.  The Promise SuperTrak EX8350 

My question is this...

If I get this Raid Card, and disable the onboard SATA ports, and move the drives over to the new RAID card in the correct order, will the system boot up and run or not.  

**NOTE** this would all be on the same system, I am not moving it to another box, just looking out for future addition of drives.  

I would still be using Mdadm RAID5 setup.  Not using RAID card bios other than to detect and see the drives.  

Has amnyone ever tried this or something similar?  please advise.

---

### Post by WhaleVPS on 2013-03-26
If you just straight jump the drives over and set the RAID card up as "RAID0" then it should boot. You may have to play with the order the drives are connected though so that sda1 links to x and such. If you want to use the RAID card fully though (RAID 1 / 5 / 6) you are going to have to most likely wipe data from the drives.

If I were you I'd make a full backup of the data then try. You will probably need to recreate the partitions on the drives and such to get this working. I'm not a file system expert though.

---

### Post by Cheesemill on 2013-03-26
If you are just using your new card to pass the single disks through to your OS and you aren't using any of its RAID features (good idea as it's likely to be SoftRAID anyway) then you shouldn't have any problems. Mdadm should automatically assemble your RAID5 when you boot.
AFAIK mdadm uses UUID's to assemble the array, so it shouldn't matter if the device names of your drives change.

---

### Post by darkod on 2013-03-26
Just make sure the adapter supports pass-through since with some adapters you HAVE TO configure a raid array. In that case it will not serve the purpose.

Also, make sure it has enough bandwidth to support your raid, sometimes the sata ports on the board will be better. On the other hand if the adapter is SATA3 and you want to use that it might be better to move them, although mechanical disks don't come close to saturating SATA2. In raid5, maybe, haven't looked into the math.

Consider the bandwidth the controller supports especially if you plan to use all 8 ports in the future. Depending on the PCI-X port (1x, 4x, 8x) it might not be fast enough for 8 disks.

---

