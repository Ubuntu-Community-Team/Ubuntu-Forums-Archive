---
title: "Howto add existing data on RAID5 to new install of ubuntu server"
date: 2011-05-25
forum: Server Platforms
---

### Post by t.h.w. on 2011-05-25
Hi,

As a newbie, I am having some trouble with my RAID 5 server.
Everything worked fine, until power was cut-off (working on electrics in the street) and my server wouldn't boot. 

I used to use the RAID as storage over LAN to backup files. Used is as /home as I was the only user. / and swap are on a separate drive, this seemed safe, in case I ever needed to install server again... To cut a long story short: I now ended up installing Server 9.10 again.

The partitions of the RAID 5 array are visible, I chose 'add software RAID', did choose the corresponding partitions, but after install: nothing. /dev/md0 does not exist, superblocks are missing, etcetera...

I would like to have my server up and running again, with the RAID 5 again as /home (accessible through my LAN), and with the existing data. I don't mind installing Server again, if this is the easiest option...

Can I safely use 'mdadm --create' without loosing data? --assemble doesn't work, as /dev/md0 'doesn't exist'...

I know this is very rough infomormation, but after a day of google-ing, I don't know anymore what to do...

Thanks for any suggestions!

---

### Post by psusi on 2011-05-25
9.10 has reached end of life and is no longer supported.  You should install 10.04, 10.10, or 11.04.

---

### Post by t.h.w. on 2011-05-25
@psusi: Ok, no problem, I have already downloaded that. Is there in 10.04LTS/11.04LTS Server a simple solution for my problem? Thanks!

---

### Post by psusi on 2011-05-25
11.04 is not an LTS, and no, it does not contain a simple solution.

mdadm --create will likely cause data loss.  Try mdadm --scan.

---

### Post by t.h.w. on 2011-05-25
> **psusi said:**
> 11.04 is not an LTS, and no, it does not contain a simple solution.

mdadm --create will likely cause data loss.  Try mdadm --scan.

mdadm --scan gives no output: 'scan does not set the mode' 
I tried instead: mdadm --assemble --scan but this gives the error: failed to create /dev/md0


When installing Server, I wanted to make the following partitions:
drive 1: two partitoins: / and swap
drive 2: raid
drive 3: raid
drive 4: raid

On the raid I would like to have /home, as I had before.
I have the feeling I missed something when installing...

---

### Post by psusi on 2011-05-25
Oops, you need a -E in there too.

---

### Post by aphatak on 2011-05-25
If you are using RAID5, I would suggest a UPS.  Apparently RAID5 is a delicate beast, and if power fails while you are writing to it, your RAID5 array can get seriously screwed up.  I should know - I learnt it the hard way!  The only reason I retained my sanity was, I take a nightly backup on a physically separate server, and I could copy the data back after re-building the array and reformatting it.

---

### Post by psusi on 2011-05-25
> **aphatak said:**
> If you are using RAID5, I would suggest a UPS.  Apparently RAID5 is a delicate beast, and if power fails while you are writing to it, your RAID5 array can get seriously screwed up.  I should know - I learnt it the hard way!  The only reason I retained my sanity was, I take a nightly backup on a physically separate server, and I could copy the data back after re-building the array and reformatting it.

Umm... no?

A UPS is always a handy thing to have, but the whole point of RAID is to be MORE robust than a single disk, not less.

---

### Post by aphatak on 2011-05-26
If only one disk fails (perhaps because of a hardware fault) RAID5 *is* more robust that having a single hard disk.  The failed disk will be reported, and your data will continue to be accessible.  You will have time to replace the failed hard disk with a new one.  Once you add the new drive to the array, the array will be re-built in the background; you can continue to use the array in the meanwhile.

If you have two disks fail in a RAID5, you stand to lose all your data.  If power fails while data is being written, this can happen.  I use RAID5 on my file-server, which stores critical data that I do not want to lose *ever*, which is my reason for recommending a good UPS for a RAID array.

---

### Post by t.h.w. on 2011-05-26
Hi,
I don't know what a UPS is, but at the moment I am installing 10.04LTS server.

I have the following drives:
1: 4 GB solid state, for the server-part
2: 1 TB for raid
3: 1 TB for raid
4: 1 TB for raid

I want to use the raid as my /home, accessible via nfs, over my lan. 

When partitioning I have the following:
drive 1:
 3 gb ext 4 for /, formatting
 1 gb swap
drive 2, 3, 4 (sdb1. sdc1. sdd1):
 raid, K (keep data?!)

When choosing 'configure raid' I only see sdc1 and sdd1
So, just to see, I choose 'remove md'. A warning appears and a md0 is mentioned to exist, with only sdb1 in it.... OK, this is new for me...

I will now finish the install and report again later...

---

### Post by psusi on 2011-05-26
> **aphatak said:**
> 
If you have two disks fail in a RAID5, you stand to lose all your data.  If power fails while data is being written, this can happen.

A power failure and having two disks fail are not really related.  Whether there is a write going on at the time doesn't matter either.

> **aphatak said:**
> I use RAID5 on my file-server, which stores critical data that I do not want to lose *ever*, which is my reason for recommending a good UPS for a RAID array.

RAID is no substitute for backups, so if it is really critical then I hope you're also making regular backups.  Most people seem to think that raid makes sure their data will not be lost, when the truth is that the point of raid is more to maintain uptime, not protect data.

> **t.h.w. said:**
> Hi,
I don't know what a UPS is, but at the moment I am installing 10.04LTS server.


Uninterruptable Power Supply, aka battery backup.

---

### Post by t.h.w. on 2011-05-26
Ah, UPS... yes something to install...

But at the moment I still have my problem with the raid.

How can I see if the md0 is there and its status?
I did 'sudo fdisk -l'
four drives appear:
sda bootable with two partitions
sdb, sdb, sdc, are shown as Linux raid autodetect

What to do next?

---

### Post by psusi on 2011-05-26
sudo mdadm --run --scan

---

### Post by t.h.w. on 2011-05-26
> **psusi said:**
> sudo mdadm --run --scan

response: mdadm: No devices given

should I specify the three drives?

Tried:
sudo mdadm --run --scan /dev/md0
not enough operational devices for md0 (2/3 failed)


I assume this has something to do with the drives not being in the MD when installing, only sdb was in md0. How can I correct this?

Or is this the time to use --assemble ??


When: mdadm --stop --scan
mdadm: error opening /dev/md0: permission denied

Any suggestions?

---

### Post by psusi on 2011-05-26
I think you trashed your data.

---

### Post by t.h.w. on 2011-05-26
> **psusi said:**
> I think you trashed your data.

Any other suggestions than giving up?
I found people who used --force wih the command...

---

### Post by t.h.w. on 2011-05-27
Ok, I found more information:

```
sudo mdadm --query --detail /dev/md0
```
Output:
md0
raid 5
superblock is persistant
active degraded Not Started
drive 1 active sync
drive 2 removed
drive 3 removed


Now is my question how to add the other two drives.

Thanks!

---

### Post by psusi on 2011-05-27
What does sudo mdadm -E /dev/sd? say?

---

### Post by t.h.w. on 2011-05-27
> sudo mdadm -E /dev/sd?

No superblock on either drives...

(There is suddenly a strange smiley in the subject...)

---

### Post by fjgaude on 2011-05-27
I can't say what has happened, but I think you are over your head.

My only suggestion would be this:

```
sudo mdadm --assemble -f --scan
```

The -f is for force.

You still have the /**etc/mdadm/mdadm/conf** file?

---

### Post by t.h.w. on 2011-05-27
@fjgaude:
How can I see if I still have the mdadm.conf file and what there is in it? 
I am not very used to work with the terminal (yet... :) )

---

### Post by psusi on 2011-05-27
Oops, you're using partitions rather than the whole disk... run the mdadm -E on the disk partitions ( sda1? ).

---

### Post by t.h.w. on 2011-05-27
```
cat /etc/mdadm/mdadm.conf
```
No such file
```
cat /etc/mdadm/mdadm/conf
```
No such file


```
sudo mdadm -E /dev/sdb1
```
....
status clean
checksum correct
sdb1 active sync
sdc1 faulty removed
sdd1 faulty removed
...

```
sudo mdadm -E /dev/sdc1
```
....
status clean
checksum correct
sdb1 active sync
sdc1 active sync
sdd1 faulty removed
...

```
sudo mdadm -E /dev/sdd1
```
....
status clean
checksum correct
sdb1 active sync
sdc1 active sync
sdd1 active sync
....

Funny: When I check the first one (sdb1) again, the output is again:
status clean
checksum correct
sdb1 active sync
sdc1 faulty removed
sdd1 faulty removed

---

### Post by psusi on 2011-05-27
Please post the exact results, not a summary.

---

### Post by t.h.w. on 2011-05-27
Sorry... see below:

```
sudo mdadm --query --detail /dev/md0
```
Version: 00.90
create time: sun feb 28 15:39:31 2010
raid level: raid 5
used dev size: 976759936 (931.51 GiB 1000.20 GB)
raid devices: 3
total devices: 1
preferred minor: 0
persistance: superblock is persistant

update time: tue may 24 15:54:00 2011
state: active, degraded, Not Started

active devices: 1
working devices: 1
failed devices: 0
spare devices: 0

layout: left symetric
chunk size: 64k
UUID: f896d6e5:388d491f:6bcc90a3:a330ac83
events: 0.7288949

Number major minor raiddevice state
0        8     17     0        active sync
1        0     0      1        removed
2        0     0      2        removed



```
sudo mdadm -E /dev/sdb1
```
magic: a92b4efc
version: 00.90.00
UUID: f896d6e5:388d491f:6bcc90a3:a330ac83
create time: sun feb 28 15:39:31 2010
raid level: raid 5
used dev size: 976759936 (931.51 GiB 1000.20 GB)
array size: 1953519872 (1863.02 GiB 2000.40GB)
raid devices: 3
total devices: 2
preferred minor: 0

update time: tue may 24 15:54:00 2011
state: clean
active devices: 1
working devices: 1
failed devices: 2
spare devices: 0
checksum: bdca831f - correct
events: 7288949
Number major minor raiddevice state
0        8     17     0        active sync /dev/sdb1
1        0     0      1        faulty removed
2        0     0      2        faulty removed


```
sudo mdadm -E /dev/sdc1
```
magic: a92b4efc
version: 00.90.00
UUID: f896d6e5:388d491f:6bcc90a3:a330ac83
create time: sun feb 28 15:39:31 2010
raid level: raid 5
used dev size: 976759936 (931.51 GiB 1000.20 GB)
array size: 1953519872 (1863.02 GiB 2000.40GB)
raid devices: 3
total devices: 2
preferred minor: 0

update time: tue may 24 15:54:00 2011
state: clean
active devices: 2
working devices: 2
failed devices: 1
spare devices: 0
checksum: bdca82c8 - correct
events: 7288949
Number major minor raiddevice state
0        8     17     0        active sync /dev/sdb1
1        8     33     1        active sync /dev/sdc1
2        0     0      2        faulty removed


```
sudo mdadm -E /dev/sdd1
```
magic: a92b4efc
version: 00.90.00
UUID: f896d6e5:388d491f:6bcc90a3:a330ac83
create time: sun feb 28 15:39:31 2010
raid level: raid 5
used dev size: 976759936 (931.51 GiB 1000.20 GB)
array size: 1953519872 (1863.02 GiB 2000.40GB)
raid devices: 3
total devices: 3
preferred minor: 0

update time: [COLOR="Red"]EDIT:**march 24 2011**[/COLOR]
state: clean
active devices: 3
working devices: 3
failed devices: 0
spare devices: 0
checksum: bd4727a4 - correct
events: 5630287
Number major minor raiddevice state
0        8     17     0        active sync /dev/sdb1
1        8     33     1        active sync /dev/sdc1
2        0     8      49       active sync /dev/sdd1



The events on sdd1 differ from sdb1 and sdc1

---

### Post by psusi on 2011-05-27
It looks like sdd dropped from the array some time ago, and then sdc failed as well.  Try mdadm /dev/md0 --re-add /dev/sdc1, and if that works, fsck the filesystem, and if that looks good, mount it and make sure your files are intact.  If that all goes well, then re-add sdd and the array should recover.

---

### Post by fjgaude on 2011-05-27
> **psusi said:**
> It looks like sdd dropped from the array some time ago, and then sdc failed as well.  Try mdadm /dev/md0 --re-add /dev/sdc1, and if that works, fsck the filesystem, and if that looks good, mount it and make sure your files are intact.  If that all goes well, then re-add sdd and the array should recover.

Praise the Lord but do pass the ammunition. I hope this works, not knowing why one of the partitions or even two went bad in the first place.

Wonder what happened to the mdadm.conf file?

---

### Post by t.h.w. on 2011-05-28
```
sudo mdadm /dev/md0 --re-add /dev/sdc1
```
Output: 
re-added /dev/sdc1 HURRAY! :P \\:D/

Ok, now you say I have to fsck the lot? 

Is this the correct thing to do? 
```
# shutdown -rF now
```

:-k

---

### Post by psusi on 2011-05-29
> **t.h.w. said:**
> ```
sudo mdadm /dev/md0 --re-add /dev/sdc1
```
Output: 
re-added /dev/sdc1 HURRAY! :P \\:D/

Ok, now you say I have to fsck the lot? 

Is this the correct thing to do? 
```
# shutdown -rF now
```

:-k

No, run e2fsck -f /dev/md0

---

### Post by t.h.w. on 2011-05-29
EDIT #25:
Checked some again: The update time of drive sdd1 was 24 march 2011... So this drive had dropped out a while ago indeed...

Ok, going on:

```
sudo e2fsck -f /dev/md0
```
output:
Invalid argument while ttrying to open /dev/mdo
The superblock cannot be opened or dose not describe a correct ext2 filesystem.

e2fsck suggests to use an extra argument -b 8193 
 
More info:
I found: [http://www.linuxdoc.org/HOWTO/Software-RAID-0.4x-HOWTO-4.html](http://www.linuxdoc.org/HOWTO/Software-RAID-0.4x-HOWTO-4.html)
> Since the disks in a RAID-4 or RAID-5 array do not contain a file system that fsck can read, there are fewer repair options.** You cannot use fsck to do preliminary checking and/or repair** 


What to do next? 
How can I check the first two drives in the raid?
Or shall I just forget checking and just re-add the third drive?

Thanks!

---

### Post by psusi on 2011-05-29
Did the array actually start?  See what mdadm -D /dev/md0 says.  You might need to --run it.

---

### Post by t.h.w. on 2011-05-30
Hi! Was away working, so it took a while before I could try anything again. I hope this looks good:

```
sudo mdadm -D /dev/md0
```

output:

Version: 00.90
create time: sun feb 28 15:39:31 2010
raid level: raid 5
used dev size: 976759936 (931.51 GiB 1000.20 GB)
raid devices: 3
total devices: 2
preferred minor: 0
persistance: superblock is persistant

update time: tue may 24 15:54:00 2011
state: active, degraded, Not Started

active devices: 2
working devices: 2
failed devices: 0
spare devices: 0

layout: left symetric
chunk size: 64k
UUID: f896d6e5:388d491f:6bcc90a3:a330ac83
events: 0.7288949

Number major minor raiddevice state
0 8 17 0 active sync dev/sdb1
1 8 33 1 active sync dev/sdc1
2 0 0 2 removed


What to do next? Can you tell me how I check the filesystem? Or can I just re-add sdd1, or add sdd1? ssd1 is still behind offcourse...
Thnx!

---

### Post by psusi on 2011-05-30
You need to start the array with mdadm --run /dev/md0

---

### Post by t.h.w. on 2011-05-31
```
sudo mdadm --run /dev/md0
```

The array started!
output:
[397589.166926] raid5: raid-level 5 set md0 active with 2 out of 3 devices, algorithm 2



```
sudo mdadm -D /dev/md0
```

output:

Version: 00.90
create time: sun feb 28 15:39:31 2010
raid level: raid 5
used dev size: 976759936 (931.51 GiB 1000.20 GB)
raid devices: 3
total devices: 2
preferred minor: 0
persistance: superblock is persistant

update time: tue may 31 07:31:56 2011 (TODAY! :D )
state: clean, degraded

active devices: 2
working devices: 2
failed devices: 0
spare devices: 0

layout: left symetric
chunk size: 64k
UUID: f896d6e5:388d491f:6bcc90a3:a330ac83
events: 0.7288949

Number major minor raiddevice state
0 8 17 0 active sync dev/sdb1
1 8 33 1 active sync dev/sdc1
2 0 0 2 removed


:confused: For my understanding: The array needs to be active before you can add or re-add an extra drive? Is it now possible to do the filesystemcheck as you mentioned?
Thanks!

EDIT:
Next I am trying to fsck the array

```
sudo e2fsck -f /dev/md0
```

It is now testing:
Pass 1 to 5 without errors :)
output:
 /dev/md0: 34400/122101760 files (48,9% non-contiguous), 362617545/488379968 blocks


:confused: Is this the moment I add or re-add the third drive sdd1 (which was lagging behind)? 
Or do I have to stop the raid first, before adding the third drive?

Thanks!

---

### Post by psusi on 2011-05-31
You should be able to re-add the third drive and it will start resyncing, presuming that the drives are actually all ok.  I suggest backing up your data now, and running the long SMART self tests on all 3 drives, then if that checks out, re-add the third drive.

---

### Post by t.h.w. on 2011-05-31
> **psusi said:**
> You should be able to re-add the third drive and it will start resyncing, presuming that the drives are actually all ok.  I suggest backing up your data now, and running the long SMART self tests on all 3 drives, then if that checks out, re-add the third drive.

Ok, than I will have to mount it first and try to access it to make a backup. After I've done that, do I have to stop the array before adding the third drive, or do I hot-add it? 

EDIT:
And do I have to add the drive or do I re-add the drive? (What is the difference between adding and re-adding? In my situation the drive was in the array, but is lagging behind...)

EDIT 2:
Found this:
[http://ubuntuforums.org/showthread.php?t=1283619](http://ubuntuforums.org/showthread.php?t=1283619)

Is it wise to: 
```
sudo mdadm --detail --scan >> mdadm.conf
```

EDIT 3:
I've installed smarttools, but unfortunantely my drives do not support SMARTtools...

---

### Post by psusi on 2011-05-31
> **t.h.w. said:**
> Ok, than I will have to mount it first and try to access it to make a backup. After I've done that, do I have to stop the array before adding the third drive, or do I hot-add it? 

You can hot-add it.

> **t.h.w. said:**
> EDIT:
And do I have to add the drive or do I re-add the drive? (What is the difference between adding and re-adding? In my situation the drive was in the array, but is lagging behind...)

I believe that either will work, but the re-add may sync up faster.

> **t.h.w. said:**
> EDIT 2:
Found this:
[http://ubuntuforums.org/showthread.php?t=1283619](http://ubuntuforums.org/showthread.php?t=1283619)

Is it wise to: 
```
sudo mdadm --detail --scan >> mdadm.conf
```


Only if the array is missing from your mdadm.conf.

> **t.h.w. said:**
> EDIT 3:
I've installed smarttools, but unfortunantely my drives do not support SMARTtools...

Are you sure?  Pretty much EVERY drive made in the last 8 years or so supports SMART.

---

### Post by t.h.w. on 2011-06-01
> 
EDIT 3:
I've installed smarttools, but unfortunantely my drives do not support SMARTtools...

> Are you sure? Pretty much EVERY drive made in the last 8 years or so supports SMART. 


I've checked again:
```
sudo smartctl -i /dev/sdX
``` for every drive, and all responded that SMART is not supported.
Is this possible because the drives are usb-driven?

---

### Post by t.h.w. on 2011-06-01
OK, I hot-added the last drive and it is now rebuilding :D (This will take some time :popcorn:)

Next question is:
How to mount the array?
When installing the / and swap I couldn't specify any other mountpoint to the array, because of my known problems with the array.

The original array was build in 9.10, so the filesystem of /dev/md0 is probably ext3? How can I check this, to be sure?

---

### Post by psusi on 2011-06-01
> **t.h.w. said:**
> I've checked again:
```
sudo smartctl -i /dev/sdX
``` for every drive, and all responded that SMART is not supported.
Is this possible because the drives are usb-driven?

Ahh yes, USB is a POS.  Avoid it at all costs.  It doesn't actually pass the normal ATA hard disk commands; it only understands read and write.  USB is also slow and can only process one command at a time.  eSATA is MUCH better.

Some of the USB HD bridges have workarounds for SMART though.  IIRC, smartctl has a switch to ask it to use those workarounds... that might get it going.

You mount it the same way you mount anything; by adding it to /etc/fstab and rebooting, and/or using the mount command.

If you are still on the livecd, then run sudo mount -t ext4 /dev/md0 /mnt, or why not just reboot from the now repaired hard disks?

---

### Post by tgalati4 on 2011-06-01
SMART doesn't work over USB.   You shouldn't use USB drives for any RAID configuration.

---

### Post by t.h.w. on 2011-06-01
@tgalati4: Clearly people tend to do things they shouldn't when on a budget... I'm learning all the time...

@psusi:
> 

You mount it the same way you mount anything; by adding it to /etc/fstab and rebooting, and/or using the mount command.

Ok, I'll dive into that.... I am not familiar with the terminal, but learning...

Add the following in /etc/fstab (via vi? that'll be a new learning-curve)

/dev/md0 /mymountpoint ext3 defaults 0 0

Question: Is it ext3 or ext4 or even ext2??

> 
If you are still on the livecd, then run sudo mount -t ext4 /dev/md0 /mnt, or why not just reboot from the now repaired hard disks?

No, I am not on a live cd. My system is like this (clearly on a budget :)):

*Server-part*: sda1 = a 4GB compactflash on an IDE-port in an old laptop, with 10.04 server on it: / and swap. 
*Storage-part*: sdb1, sdc1, sdd1 are 1TB usb-drives that I use as storage (NAS) over NFS.

After noticing the problems and not knowing how to resolve them, I installed the server-part again (now with 10.04 server, instead of 9.10), and that was the moment I couldn't partition and/or set a mountpoint for the raid, because it was degraded (as we/you determined later).

So now it is 'running' again, I would like to mount the /dev/md0 again, as it has no mountpoint yet, it just sits there rebuilding. 

After mounting it, I want to set up the NFS-part again to access it again from my network.

Thanks!

---

### Post by psusi on 2011-06-01
> **t.h.w. said:**
> 
Add the following in /etc/fstab (via vi? that'll be a new learning-curve)

/dev/md0 /mymountpoint ext3 defaults 0 0


Yes, though you might want to use the UUID instead of /dev/md0.

Also nano is a lot easier to use than vi, and I highly recommend emacs over vi.  It also has quite a learning curve but is a little more friendly and a lot more powerful than vi.

> **t.h.w. said:**
> 
Question: Is it ext3 or ext4 or even ext2??


It almost certainly isn't ext2.  If you specify ext4, it will work just fine if it actually is ext3 ( or even ext2 ).

---

### Post by t.h.w. on 2011-06-02
OK, I am up and running again!\\:D/ Thanks for all the suppport!

Now, to keep me posted on the health of my array I've read it is possible to get an e-mail when things go wrong... Suggestions how I can do this?

I've added via nano in mdadm.conf the line:
MAILADDR {my_mail@provider.com}

But this does not seem to do anything (yet...)

Thanks!

---

### Post by psusi on 2011-06-02
You need to have a mail server installed, like postfix.

---

### Post by t.h.w. on 2011-06-03
> **psusi said:**
> You need to have a mail server installed, like postfix.

Thanks, I'll look into that!
First I'll close this thread with a [SOLVED] and if I need further help with the mailserver I'll start a new thread.

Thanks for all the support and advice!

---

