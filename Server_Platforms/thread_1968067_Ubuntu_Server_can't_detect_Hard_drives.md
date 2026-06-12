---
title: "Ubuntu Server can't detect Hard drives"
date: 2012-04-28
forum: Server Platforms
---

### Post by JasonMarquez on 2012-04-28
[FONT=Verdana][SIZE=2]I'm very new to servers, but I just bought one today so I could start learning. I have an 
[/SIZE][/FONT]**[FONT=Verdana][SIZE=2]IBM xSeries 346 (8840E1U) Server[/SIZE][/FONT]**

and when I enter the setup for Ubuntu, I come to the partitioning section and it cannot detect my hard drives. On there server there are 6 hard drives that are connected. I believe it cannot detect the raid or perhaps raid has not been setup yet. I don't entirely know.


Please someone help me.

---

### Post by volkswagner on 2012-04-28
Yes, it is likely RAID is not setup.

If you boot a live cd you can find out what the raid controller is.

Boot the live CD, open a terminal and run:
```
lspci
```


Also pay close attention when you first boot up.  You should see a message such as press (ctrl + S) to configure RAID.

---

### Post by JasonMarquez on 2012-04-28
I'm in the Disk Utility and I'm trying to format the filesystem for Raid, but it doesn't allow me to because it is busy. I try to unmount, but it says it's busy as well.

The filesystem is called squashfs. What is that?

---

### Post by d4m1r on 2012-04-29
Google it, a special kinds of file system.

Did you purchase this server locally and installed it at home or are you renting it from an online provider?

---

### Post by volkswagner on 2012-04-29
> **JasonMarquez said:**
> I'm in the Disk Utility and I'm trying to format the filesystem for Raid, but it doesn't allow me to because it is busy. I try to unmount, but it says it's busy as well.

The filesystem is called squashfs. What is that?


It may be helpful if you tell us the type of RAID card installed.  You'll also want to verify if Ubuntu supports the card.

I have never had a disk busy error using the RAID BIOS utility.  The typical steps would be to initialize the drive, then create the RAID array.

---

### Post by NicholasFake on 2013-02-21
Hi there !

Currently I'm facing an issue which my company server is unable to detect the exist of hard disk during reformatting.
Anyone got any solution for this ?
The server is HP StorageWork x1400 Raid Server(according to my supervisor, as I'm new to server stuff).

p.s : How are we able to find whether our hard disk existing or not through Bios ?

Please help.

---

### Post by M0pax on 2013-02-22
I have a IBM server as well. I have a CD for the config of the raid, you have to boot from that to config the raid layout, then install ubuntu.
the CD can be down loaded from IBM. hope this helps

---

