---
title: "Recover 9TB RAID5 from HP SmartArray to Linux RAID"
date: 2013-04-10
forum: Server Platforms
---

### Post by litch84 on 2013-04-10
Well, this should be a nice hard one for those gurus out there :) - Thanks in advance for helping.

4 x 3TB RAID 5 array on a HP Smart Array P410/512.

Anyway, long story short, removed a disk and it marked the array failed, no support for HP controller in HP forums so I cracked the shits and put the drives on the mobo to be recovered in Linux using mdadm... another bad idea so it would seem.

I did an "mdadm --examine --scan" and PRESTO the array (or what I though was) was listed. So I then did a "mdadm --assemble --scan" and it mounted an array on /dev/md/ddf0 and immediately started to repair it! This was NOT what I wanted, and about 30 seconds passed and I managed to --stop it (disassemble the array).

Upon further inspection, mdadm detected an old Intel RAID superblock. Great, now the first 100MB of my array is garbage...

My options were running out, and I manually specified the --create flags with an external bitmap so it didn't write to the drives. I tried 128K and 256K strip with all known parity methods (left/right*asym/sym) and used gdisk (the GPT sister of fdisk) to sample the array (it should pick up the backup GPT at the end of the drive if the array is assembled correctly):
```
Example:
mdadm --create --assume-clean --bitmap=/root/test.bmp -c 128 -l 5 -n 4 -f -R -p left-asymmetric /dev/md0 /dev/sdd /dev/sdb /dev/sde /dev/sdf
```
- but no, mdadm still wrote data to the disks and I still had no GPT partitions appear when I ran gdisk.

The thing is, /dev/sdd (The first disk in the original array) has the valid GPT partition on it, at offset 0x200 (bytes).

So here I am, pleading for help with getting these 9TB of data back.

I have:
[LIST]
[*]The diagnostic output of the HP Controller for the array before it went kaput (attached)
[*]From that, I have the known order of the disks in the original array:
[/LIST]
```

#1 SerialNo=Z1F0NL2Y /dev/sdd
#2 SerialNo=Z1F0NNXW /dev/sdb
#3 SerialNo=Z1F0NKHN /dev/sde
#4 SerialNo=Z1F0NW23 /dev/sdf


```
[LIST]
[*]The original GPT partition backed up from /dev/sdd:
[/LIST]
```
First usable sector is 34, last usable sector is 17581400974
Partitions will be aligned on 8-sector boundaries
Total free space is 0 sectors (0 bytes)


Number  Start (sector)    End (sector)  Size       Code  Name
   1             128     17581400974   8.2 TiB     0700  primary




```
[LIST]
[*]and some amount of corrupt data at the start of the array.
[/LIST]

The first step:
1. Some way to verify that I can assemble this array correctly without corrupting the data any further.

The second step:
2. Scan for a ext4 superblock and repair the file system.

The third step:
3. Mount it, continue using Linux RAID.

Fourth:
4. Beer

---

### Post by darkod on 2013-04-10
Unfortunately I don't think you can recover HW raid data with mdadm. That's why you need to use mdadm from the start.

I also wonder (but it's too late now, I know) how would one failed disk fail a raid5 array. It should happily keep going with one disk missing, that's the point.

Wait a bit longer if someone jumps in, but i have never seen this done so far (which doesn't make it impossible of course).

---

### Post by cerealcable on 2013-04-10
Not certain what you have on the array, but hopefully you have a backup (RAID is unfortunately not a backup solution itself).  If you have a backup, even if it is outdated you'll likely save money and time just rebuilding the array and using it that way.

Darko is correct, mdadm isn't the tool to recover an array from a hardware card.  9 TB is a lot, you likely needed to recover it via the hw, usually you can force arrays online even if they have a failed drive (hence the point of RAID 5).  My only real suggestion is to contact HP and pony up the money for support unless you've got a backup of the data.  Otherwise, you are likely looking at paying a data recovery specialist to manually reassemble the data, and that will be very pricey.

I'm sure there is a way to do it, I unfortunately do not know the way and it'd probably have to be specific to your RAID card and firmware as they all can work slightly differently with the data on the disk.

Best of luck o_O

---

### Post by litch84 on 2013-04-10
> **cerealcable said:**
> (RAID is unfortunately not a backup solution itself).

Spare me the speech.

The data is re-obtainable, it's just a matter of time more than anything - hence I couldn't justify having another $700 worth of 9TB laying around to back this up (non-business related data)

On another note, I managed to do just what you said - re-enabled the logical disk back on the RAID card. I could have punched the screen, I literally spent hours waiting for forum replies, searching for a way to do that before I attempted to mount via Linux (and ultimately corrupted the data) - I just stumbled upon it then while searching for ways to achieve my questions here...

Anyway, I've re-assembled the drive on the P410, overwrote the GPT to restore the partition, but I can't get fsck.ext4 to read the array yet... it comes up with an error:

```
root@host:~# fsck.ext4 -vyf /dev/sdg1
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Device or resource busy while trying to open /dev/sdg1
Filesystem mounted or opened exclusively by another program?

```

So I'll have to wait until I finish work and boot it with a live CD and try from there.

[EDIT]

Using debugfs I'm able to use the superblock at 512000000 and navigate the file system - just need to reboot with a live cd and see if I can get fsck going...

---

### Post by litch84 on 2013-04-12
The solution was to use dumpfs with the superblock at 512000000 and 'rdump' the directories to another filestore - took 22 hours but I recovered just about everything.

Thanks for the assistance anyway guys!

---

