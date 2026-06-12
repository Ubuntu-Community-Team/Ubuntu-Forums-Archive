---
title: "Experimenting with software RAID in VirtualBox; need help"
date: 2011-12-29
forum: Server Platforms
---

### Post by diablo75 on 2011-12-29
I just finished setting up a software RAID-1 array in Virtualbox with two 10 GB drives.  Setup and install was pretty simple and smooth.  After the system was alive I decided to do some testing.  I shut the VM off, opened up the storage settings menu and detached what was the primary drive (or rather, the drive that was on SATA port 0; the second drive being on port 1).

I started the VM back up and it sat at a cursor for about 20 seconds but then some stuff whipped by and I noticed it said it was now running in a degraded mode, proceeded to boot up otherwise normal looking.  I though, "Let's see what happens when I do this" and decided to just create an empty folder on the desktop and shut back down (to see if it would sync up later with the missing drive after bring it back to the mix).

I re-attached the primary, booted, no messages about RAID software anywhere along the way degraded mode or otherwise, looked normal.  Shutdown, removed the secondary drive this time.  When I booted up this time it takes me to a prompt that says "Error: Disk missing" and then a grub> prompt with a blinking cursor.

I'm not sure if this is what is suppose to happen in real life or if this is a quirk happening because it was simulated in VBox or if there was something I was supposed to do after re-attaching the first "bad" drive.  Any help would be greatly appreciated.

---

### Post by darkod on 2011-12-29
I haven't work with raid too much but the first thing on my mind is that after you re-attach the "bad" disk you have to wait to sync first. If you disconnected the second disk while still not synced, it will probably go crazy. :)

You can see the status of the array/sync with:

cat /proc/mdstat

PS. One more thing. If I remember correctly, before removing a disk even if it really failed totally, you need to mark it as failed in the array config. The command was something like:
sudo mdadm --manage /dev/mdX --fail /dev/sdXY

You would need to do that for every partition on the disk which is part of software raid. If testing by removing /dev/sda, you would mark fail /dev/sda1, /dev/sda2, etc in their respective arrays. Only then disconnect the disk. This should also apply to VBox.

---

### Post by idef1x on 2011-12-29
What darkod mentions sounds the logical think to check: where the disks in sync again before you took out the second drive..
Take note that syncing can take a long time, since it will sync every bit again (that's why it's called a mirror ;-) )

---

### Post by spynappels on 2011-12-29
Software RAID drives do need some managing, and syncing a drive can take quite a long time as idef1x said. 

I found the mdadm man page very helpful when I was learning about this [http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm) and you have done the right thing in learning in a virtual environment.

Have fun, and try building some RAID5 or RAID6 arrays and drop disks out, then the fun really starts!

---

### Post by rubylaser on 2011-12-29
> **darkod said:**
> I haven't work with raid too much but the first thing on my mind is that after you re-attach the "bad" disk you have to wait to sync first. If you disconnected the second disk while still not synced, it will probably go crazy. :)

You can see the status of the array/sync with:

cat /proc/mdstat

PS. One more thing. If I remember correctly, before removing a disk even if it really failed totally, you need to mark it as failed in the array config. The command was something like:
sudo mdadm --manage /dev/mdX --fail /dev/sdXY

You need to wait for the disks to resync for this to work properly.  And, you don't need to remove a disk even if it totally fails.  You just shut down the computer, remove the defective disk, then add a new one like this.

```
mdadm --add /dev/md0 /dev/sdX1
```
mdadm will know that it's missing a disk and automatically use this new disk to restore parity. Replacing disks in RAID5/6/10 arrays is equally easy to recover from.

---

### Post by diablo75 on 2011-12-29
> **darkod said:**
> You can see the status of the array/sync with:

cat /proc/mdstat



I'm in a hurry to leave the house but this command showed me that there was syncing going on in the background that I wasn't aware of.  I'm blown away by how automatic the whole thing is.  Says it's got about 8 minutes left to finish.  I'll look over the other posts soon but this is enough to show me that I at least got it created/installed/setup correctly.  Thanks!

---

### Post by jchung on 2011-12-29
To give you an idea... I have a file server at home where I have two mdadm arrays created. One is ~ 6TB (8 drive RAID 6 array) and the other is ~ 9TB (4 drive RAID 5 array).

I use a Intel(R) Celeron(R) CPU G530 @ 2.40GHz dual core processor & 4GB RAM.

I have no problems getting ~ 600MB/s reads and ~ 450MB/s writes to the 6TB array.


Joo

Sorry. Wrong thread. :)

---

### Post by diablo75 on 2011-12-29
> **rubylaser said:**
> You need to wait for the disks to resync for this to work properly.  And, you don't need to remove a disk even if it totally fails.  You just shut down the computer, remove the defective disk, then add a new one like this.

```
mdadm --add /dev/md0 /dev/sdX1
```
mdadm will know that it's missing a disk and automatically use this new disk to restore parity. Replacing disks in RAID5/6/10 arrays is equally easy to recover from.

I'm still experimenting and decided the next thing I wanted to try and pretend a disk has completely failed and to replace it with a new, empty virtual disk of the same size as the old one.  The command you mentioned above made me think/realize that it would seem I have to recreate new partitions of the same size on the replacement disk before I can add those partitions to their respective arrays.  Is that correct?  If so, what's an easy way to do that so that they match in size?

Also, out of curiosity, is it a good or a bad idea to setup software raid for the swap partition?  I originally setup two matching partitions on both drives, and having gone back and forth between them individually (running without one or another and then both again to see what happens) I'm now running with one of the original discs, one blank (which hasn't been added to any arrays yet or formated/partitioned) and the status of the md0 array shows "active raid1 sda1[1] ; 9990080 blocks [2/1] [_U]"

and the one for the swap partition shows "inactive sda5[1] (S) ; 492480 blocks".  Is this normal?  Shouldn't they both be active?  Does this mean I'm currently running without any swap partition mounted?

---

### Post by darkod on 2011-12-29
According to this: [http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

To copy the partition table (layout) of /dev/sda to /dev/sdb you do:

sudo sfdisk -d /dev/sda | sfdisk /dev/sdb

PS. About swap. The (S) means Spare, and since sdb5 is not present, there is nothing active. This might be a result of disconnecting the second disk without syncing, don't know.

---

### Post by rubylaser on 2011-12-29
> **darkod said:**
> According to this: [http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

To copy the partition table (layout) of /dev/sda to /dev/sdb you do:

sudo sfdisk -d /dev/sda | sfdisk /dev/sdb

PS. About swap. The (S) means Spare, and since sdb5 is not present, there is nothing active. This might be a result of disconnecting the second disk without syncing, don't know.

This is exactly how you'd copy over the partition table for a RAID1 array.  In RAID5/6 it doesn't matter as the size of the array is determined by the smallest member.

Also, I'd put your swap on a setup raid1 array. In this case, it looks like your swap array didn't sync, or is broken.  You could easily stop the array and recreate it.  **Caution** this is off the top of my head, so I could be forgetting a step.  Also, you'll want to ensure that md1 is the correct device.

```
mdadm --stop /dev/md1
```
then zero the superblocks
```
mdadm --zero-superblock /dev/sda5
mdadm --zero-superblock /dev/sdb5
```

Then, recreate the array.
```
mdadm --create --verbose /dev/md1 --level=1 --raid-devices=2 /dev/sd[ab]5
```

Then make it a swap partition
```
mkswap /dev/md1
```

Edit your /etc/fstab to mount this array, and update your /etc/mdadm/mdadm.conf file.
```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR  youruser@gmail.com" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Finally, setup your swap to startup on reboot
```
update-initramfs -k all -u
```

---

### Post by diablo75 on 2011-12-29
> **darkod said:**
> According to this: [http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

To copy the partition table (layout) of /dev/sda to /dev/sdb you do:

sudo sfdisk -d /dev/sda | sfdisk /dev/sdb

PS. About swap. The (S) means Spare, and since sdb5 is not present, there is nothing active. This might be a result of disconnecting the second disk without syncing, don't know.

I had to insert a sudo in front of the second sfdisk command following the pipe | symbol and it gives me an output saying it "doesn't like" what I'm proposing.  Is this normal?

```
owner@ubuntutest:~$ sudo sfdisk -d /dev/sda | sudo sfdisk /dev/sdb
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Checking that no-one is using this disk right now ...
OK

Disk /dev/sdb: 1305 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type
Old situation:
No partitions found
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *      2048  19982335   19980288  fd  Linux raid autodetect
/dev/sdb2      19984382  20969471     985090   5  Extended
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty
/dev/sdb5      19984384  20969471     985088  fd  Linux raid autodetect
Warning: partition 1 does not end at a cylinder boundary

sfdisk: I don't like these partitions - nothing changed.
(If you really want this, use the --force option.)

```

---

### Post by rubylaser on 2011-12-29
I'd just step up to the root user for running the whole command like this...
```
sudo -i
enter root password here...
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

---

### Post by diablo75 on 2011-12-29
> **rubylaser said:**
> I'd just step up to the root user for running the whole command like this...
```
sudo -i
enter root password here...
sfdisk -d /dev/sda | sfdisk -f /dev/sdb
```

I inserted the -f above where the force option needed to go to make sfdisk ignore the weirdness of the source disk (perhaps it has something to do with being a virtual drive).

Edit:  I wanted to paste in some output.  I've managed to get the primary partitions on the old drive and the new empty one with the copied partition table to sync but I wasn't able to add the new partition intended for swap to add to md1.  I think this was brushed on in a previous post but I've not read it closely enough yet.  Here's what it says:

```
root@ubuntutest:~# mdadm --add /dev/md0 /dev/sdb1
mdadm: added /dev/sdb1
root@ubuntutest:~# mdadm --add /dev/md1 /dev/sdb5
mdadm: cannot get array info for /dev/md1
root@ubuntutest:~# exit
logout
owner@ubuntutest:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : inactive sda5[1](S)
      492480 blocks
       
md0 : active raid1 sdb1[2] sda1[1]
      9990080 blocks [2/1] [_U]
      [==>..................]  recovery = 10.1% (1014592/9990080) finish=11.8min speed=12604K/sec
      
unused devices: <none>

```

---

### Post by rubylaser on 2011-12-29
md0 is the / partition and md1 is the swap partition.  It looks like you need to blow away md1, and set it up again like I mentioned on [page 1 of this thread]("http://ubuntuforums.org/showpost.php?p=11573626&postcount=10").

---

