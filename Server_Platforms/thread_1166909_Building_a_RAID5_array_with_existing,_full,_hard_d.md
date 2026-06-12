---
title: "Building a RAID5 array with existing, full, hard drives?"
date: 2009-05-22
forum: Server Platforms
---

### Post by grantemsley on 2009-05-22
I'm running Ubuntu 8.10 32bit

My file server currently has a 400GB system drive (/boot, /) which I won't be touching at all.

It also has 2 seperate, non raided 1TB drives which are nearly full. I plan on buying 2 1.5TB drives attached to a faidraid controller and use software raid.

I'd like to use the first 1TB of each of the 1.5TB drives, along with the 2 1TB drives to build a 4TB (3 usable) RAID5 drive.  But there are a couple stumbling blocks I've run into.

I don't have anywhere to store the almost 2TB of data currently on the 1TB drives.

So my plan is as follows:
[LIST]
[*]Partition the two 1.5TB drives as 1TB + 500GB (making sure the 1TB partition is the exact same size as the partitions currently on the 1TB drives).

[*] Build a RAID5 array with JUST those two drives
This is the first problem - can I build a raid5 array with just two drives temporarily to move data to it?
[*] Copy data from the first 1TB drive to the array
[*] Add the now empty drive to the array, let it rebuild, and resize the filesystem (not sure what commands do this)
[*] Repeat the copy/add/rebuild/resize procedure for the second 1TB drive
[/LIST]

Questions:
[LIST=1]
[*]Will this work without any data loss?
[*]How do I create a RAID5 array with only 2 drives so I can copy data to it?
[*]What exactly is the procedure for adding a drive and expanding the array?
[*]Are there any other steps I'm missing? Or a better way to do this?
[*]Are there any drive, partition, or file size limits I need to worry about?
[/LIST]

I've gone over most of the guides and instructions for software raid, but I'm still nervous about doing this - I don't want to lose any data (and don't have backups, not enough room on anything to store them...the really important stuff is backed up, and I won't die if I lose everything, but I'd be really upset about it!)

---

### Post by windependence on 2009-05-22
You need at least 3 drives for RAID5. Your plan looks dangerous to me. I think you're just going to have to go buy 2 1TB drives and use them for storage. You should have a place to back up your data anyway as RAID is no substitute for backup, and IMHO software RAID is worse. No flame wars here, this is just my opinion and it doesn't mean anything other than the fact that I have worked in enterprise data centers for over 15 years and there is a reason they use hardware RAID.

-Tim

---

### Post by grantemsley on 2009-05-22
> **windependence said:**
> You need at least 3 drives for RAID5. Your plan looks dangerous to me. I think you're just going to have to go buy 2 1TB drives and use them for storage. You should have a place to back up your data anyway as RAID is no substitute for backup, and IMHO software RAID is worse. No flame wars here, this is just my opinion and it doesn't mean anything other than the fact that I have worked in enterprise data centers for over 15 years and there is a reason they use hardware RAID.

-Tim

The array will eventually have 5 drives...I just need it to temporarily accept two :)  I'm not sure if this is possible...but since a 3 drive array is still usable with 2 drives (in degraded mode) I hope that it's possible to make the array in degraded mode.

I know RAID is no substitute for backups.  It will only help in the event of a single drive failure, not a catastrophic failure, nor from accidental deletion or corruption.  The stuff that's irreplaceable is backed up to an external drive.  But the rest of the 2TB of data isn't important enough to need backups.  Most of it is my VHS/DVD collection all nicely captured and reencoded.  I can do that again if I really need to...it would just take several months to rebuild it.

Hardware raid would be nice...but it's way outside of my budget, overkill for what I'm doing, and riskier if the RAID controller fails.  At least with software raid I can pop all the drives in another linux system with any SATA controller and hopefully get my data back.

The only part I'm having problems with is how to shuffle the data around so I can build the array without having somewhere else to dump the data to in the mean time.

---

### Post by windependence on 2009-05-22
You're not going to be able to set up the array in RAID5 with two drives AFAIK because you can't set up an array in degraded mode. There is a member here Figaude who is very very good at software RAID and may be able to help you with this, but I would say there is probably no way without buying a few drives. they are less than $100 now. if you can't get them that cheap, let me know and I'll point you in the right direction.

-Tim

---

### Post by grantemsley on 2009-05-22
I can get the drives that cheap...but I've already spent all I can afford on hard drives for the moment.

I've see a few people who have managed to do this, by telling mdadm to build the array with one drive missing using the command "mdadm -C /dev/md0 -l5 -n3 /dev/sda1 /dev/sdb1 missing"

I just don't know the exact procedure.

If nobody else chimes in with ideas, I guess the safest thing for me to do is create some 1 and 1.5GB virtual disks in vmware and test it in a virtual machine before doing anything to the real drives.

---

### Post by grantemsley on 2009-05-23
I've figured out how to do it.  For future searchers and my own future information, here's what you do.  I've tested this in VMware twice, using 1GB and 1.5GB drives to save time.


Assuming /dev/sdb and /dev/sdc are the existing 1TB drives.
/dev/sdd and /dev/sde are the new 1.5TB drives.

Install mdadm.


```

sfdisk -d /dev/sdb | sfdisk /dev/sdd
sfdisk -d /dev/sdb | sfdisk /dev/sde

```
This copies the partition table from one of the existing disks to the new ones, to ensure the partitions are all the same size.

Then use cfdisk to change the partition type of /dev/sdd and /dev/sde to "DA" for non filesystem data.

```
mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdd1 /dev/sde1 missing
```
The missing keyword tells mdadm that you are going to be using 3 drives, but for now, just use these two.  The array will be fully usable in degraded mode (no redundancy).

```
mkfs.ext3 -b 4096 -E stride=16 /dev/md0
```
The stride option adjusts how ext3 stores things.  It is supposed to be ideal for a 64k chunk size on the raid array.

Now mount /dev/md0 and copy all your data from the two 1TB drives to the array.  Make sure it's all there and intact because now we start deleting stuff from the old drives!

Unmount the two 1TB drives.
Using cfdisk, change the partition types for /dev/sdb and /dev/sdc to "DA".

```
mdadm --add /dev/md0 /dev/sdb1
```
This will add a third drive to the array.  mdadm automatically starts rebuilding the array to add redundancy.  You can watch /proc/mdstat to see it rebuilding.  On my 1GB drives this took about 2 minutes...so I'm guessing about 30 hours for 1TB drives!

```
mdadm --add /dev/md0 /dev/sdc1
```
Add the last drive to the array.  mdadm will mark is as a spare drive

```
mdadm ---grow /dev/md0 --raid-disks=4 --backup-file=/root/grow_md0.bak
```
Make sure the location for the backup file is on a different filesystem.  It may be used to recover if things go wrong (since things haven't gone wrong for me, I don't know how to do that...but it's probably a good idea to have that file).

Watch /proc/mdstat and it will say it is reshaping.  Took 4 minutes on 1GB drives, so estimating 66 hours for 1TB drives. When it is done, the array will show as having more blocks.

Last step is to resize the actual filesystem.
```
resize2fs /dev/md0
```
This can be done while the filesystem is still in use.  

df -h should show you have 3TB of space on /dev/md0

Disclaimer:  Messing up any step, or having a power failure or hardware problem or cosmic rays or just bad luck could cause you to lose all your data.  RAID is not a backup solution.  I recommend backing up all data first.  In my case, I'm confident enough to do it without a backup, because I simply don't have anywhere to back it up to.  But it's risky.

I hope this helps someone else looking for the same thing.

---

### Post by fjgaude on 2009-05-24
Late in getting here, but it looks good to me, grantemsley! Good job!

---

### Post by grantemsley on 2009-06-01
I built the array on the real drives this weekend and everything went great.

Using the last 500GB partition on the drives hurts performance of the raid array a bit...but this system has less than 10 users, so I'm rarely maxing out the disc anyways.

---

### Post by TwiceOver on 2009-06-01
Just came in to say DAMN you must have some big brass balls.

Don't think I could have done that.

---

### Post by grantemsley on 2009-06-01
> **TwiceOver said:**
> Just came in to say DAMN you must have some big brass balls.

Don't think I could have done that.

Well, if you can avoid doing it without backups, I'd definitely recommend that!

I was very nervous doing this.  But there were a couple reasons I went ahead with it:
[LIST]
[*] Didn't have much choice, since I couldn't afford more drives to back things up
[*] The data isn't irreplaceable.  I have backups of things like my wedding photos and such - it just would have taken months to rip all those DVDs and VHS tapes again
[*] I tested it twice in a virtual machine.  I setup the VM just like I have my server (except with 1GB drives instead of 1TB) and documented every command I typed.  Then I did it again following just my notes to make sure I didn't overlook any steps.
[/LIST]

But still, was quite nerve racking.  And watching an array rebuild for 40 something hours isn't much fun.

---

