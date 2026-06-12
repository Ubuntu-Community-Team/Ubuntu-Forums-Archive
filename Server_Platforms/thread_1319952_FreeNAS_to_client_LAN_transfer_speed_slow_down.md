---
title: "FreeNAS to client LAN transfer speed slow down?"
date: 2009-11-08
forum: Server Platforms
---

### Post by handy on 2009-11-08
I got great help in this forum many months ago, when I first setup my FreeNAS box & NFS.  So when you're on a good thing... :)

I just cloned my 320GB drive to a 1.5TB drive, using the wonderful Clonezilla. It worked very well, with a tough set of partitions:

FAT32 - GPT 
HFS+ - OS X
Ext3 - / Arch system
JFS - /home
Ext3 - /storage

My first attempt with dd, failed, in that OS X would boot, but no matter what I tried I could never get Arch to boot.  I could access the Ext3 partitions from OS X, via the Ext3 for Mac software. I tried rescue disks, super grub, you name it...?

Anyway, that's the background.

The situation now is that I am in the process of copying 290GB of data across the LAN from my FreeNAS box onto the now 1.2TB storage partition on the iMac.

The transfer speed is around 2,500 KB/s.  I was used to the speed being around 11,000 KB/s.  At the current speed I'm looking at around 30 hours to get the job done, when in reality it should have finished in a fraction of that time.

Why would the speed have changed?

The storage drive in the FreeNAS box is a WD Green 1TB, the new drive in the iMac is a WD Green 1.5TB. These are not the fastest drives around, but they are certainly not the problem here.

Any ideas on what I might be able to configure to regain the lost transfer speed on my 10/100 Mbit LAN?

---

### Post by handy on 2009-11-09
Sorry guys, I had stated my speed incorrectly in the OP. :(

I edited it & they are correct now, as follows:

Was 11,000 KB/s, is now 2,500 KB/s.

When absolutely nothing else has changed but the perfectly cloned HDD.  I just don't understand.

When the copying of my data form the FreeNAS box to the workstation is finished, I will shut down everything on my entire LAN for a while & start it back up again.  Hopefully a lack of electrons will starve the bugs!? :confused:

---

### Post by handy on 2009-11-12
I have just been moving some data into the FreeNAS box, which is historically the way data goes to be backed up here.

After noticing the slow transfer rate from FreeNAS to the client, (which is what prompted the OP in this thread) I did some tweaking of the NFS settings in Arch, only to slightly improve the transfer speed from the FreeNAS box.

Today when sending data over to the FreeNAS box I am seeing an average speed improvement of >1,500 KB/s.  Which is nice.

So I tested the FreeNAS to client speed & it is still slow. I think it has always been slow & I never noticed because I rarely send data in that direction.

I'll get around to talking on the FreeNAS forum & see what I can do to adjust the server settings.

---

