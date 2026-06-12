---
title: "Installing new harddrive"
date: 2009-08-05
forum: Server Platforms
---

### Post by bestdayever on 2009-08-05
Well I have a small server I set up to be a little home fileserver.

Heres the problem, the computer is so old I actually have a pci card to hold ide harddrives, now I just popped in a 500gb WD hd and its not recognizing it.

When I do a fdisk -l All it sees is my single 80gb hd.

What am I doing wrong, or is that some sort of card compatibility issue?

---

### Post by peekaboo on 2009-08-05
Does it appear in the bios?

---

### Post by giggins on 2009-08-05
Several older IDE controllers can't handle drives with a capacity over 137GB. See this [Wikipedia article]("http://en.wikipedia.org/wiki/Parallel_ATA#Drive_size_limitations") for more info.

---

### Post by bestdayever on 2009-08-05
> **giggins said:**
> Several older IDE controllers can't handle drives with a capacity over 137GB. See this [Wikipedia article]("http://en.wikipedia.org/wiki/Parallel_ATA#Drive_size_limitations") for more info.


Oh, well thanks for the quick answer, guess I gotta upgrade or buy a new pci card:P.

---

### Post by giggins on 2009-08-05
Check if the PCI card is ATA-6 or better. If its not, that'll be your problem, in all likelihood.

---

### Post by bestdayever on 2009-08-07
Well I checked up on the  card, and according to this site it is ATA-6.

[http://www.powersourceonline.com/buy-equipment/promise-tech-Parts/ULTRA100TX2/31777791-ULTRA100TX2-cy-en.jsa](http://www.powersourceonline.com/buy-equipment/promise-tech-Parts/ULTRA100TX2/31777791-ULTRA100TX2-cy-en.jsa)

Any other ideas?

---

### Post by giggins on 2009-08-07
Is your 80GB drive attached to the PCI PATA controller, or an onboard controller?

Also, 'fdisk -l' only lists partition tables. If the new disk has never been "initialized" (meaning its never had a partition table created), then you may need to do that first...

```
sudo fdisk /dev/hdb
Command (m for help): o

```

Make sure '/dev/hdb' would be the next disk. The "o" command creates a new partition table on the disk. From there, you can start adding partitions then formatting them.

---

### Post by bestdayever on 2009-08-07
> **giggins said:**
> Is your 80GB drive attached to the PCI PATA controller, or an onboard controller?

Also, 'fdisk -l' only lists partition tables. If the new disk has never been "initialized" (meaning its never had a partition table created), then you may need to do that first...

```
sudo fdisk /dev/hdb
Command (m for help): o

```Make sure '/dev/hdb' would be the next disk. The "o" command creates a new partition table on the disk. From there, you can start adding partitions then formatting them.

Well I tried that and it said that no drive exists. Could it possibly be the jumpers on the drive? I have never really had to set them to the slave or master setting but would that effect it if I did?

---

### Post by giggins on 2009-08-07
Jumpers can definitely cause issues. What IDE / PATA devices are on this machine? Do you have a CD-ROM drive on PATA too?

You should *probably* have your 80GB drive set as Master (primary) since it likely has your bootloader on it, your 500GB drive as Slave (secondary), and your CD-ROM drive as Master on a different IDE channel. 

If the 80GB drive is set to Cable Select (often just called CS), but your 500GB drive is set to Master, then it could be causing your issue. I would make sure you have properly configured the drives in the above mentioned configuration to continue troubleshooting your issue.

Write down the current position of the jumper on the 80GB IDE drive if you move it, because it works now, and I'd hate for you to move the jumper and forget where it was, especially if the drive doesn't have clear markings for which pins are what.

---

### Post by garfonzo on 2009-08-07
> **giggins said:**
> Jumpers can definitely cause issues. What IDE / PATA devices are on this machine? Do you have a CD-ROM drive on PATA too?

You should *probably* have your 80GB drive set as Master (primary) since it likely has your bootloader on it, your 500GB drive as Slave (secondary), and your CD-ROM drive as Master on a different IDE channel. 

If the 80GB drive is set to Cable Select (often just called CS), but your 500GB drive is set to Master, then it could be causing your issue. I would make sure you have properly configured the drives in the above mentioned configuration to continue troubleshooting your issue.

Write down the current position of the jumper on the 80GB IDE drive if you move it, because it works now, and I'd hate for you to move the jumper and forget where it was, especially if the drive doesn't have clear markings for which pins are what.

That's exactly what happened to me. I spent the better part of half a day trying to figure out why my drive wasn't recognized. Then I changed the jumpers and all was perfect.

---

### Post by bestdayever on 2009-08-07
> **garfonzo said:**
> That's exactly what happened to me. I spent the better part of half a day trying to figure out why my drive wasn't recognized. Then I changed the jumpers and all was perfect.


Alright, thanks for the advice, I'm gonna give it a shot and post the results after I get another IDE cable. (2 have broken on me while trying to figure this out, hah)

---

