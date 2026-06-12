---
title: "Repair Degraded Raid 5 w/ mdadm"
date: 2009-10-17
forum: Server Platforms
---

### Post by zackiv31 on 2009-10-17
One of my drives got kicked out of the array and I want to put it back into it, relevant info is below... Drives are sd[abcd]1

```

me@me:~$ sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 00.90
  Creation Time : Tue May 12 23:47:18 2009
     Raid Level : raid5
     Array Size : 2197715712 (2095.91 GiB 2250.46 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 17 13:43:25 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 55291172:b3b9b755:10f5c018:28823fe1 (local to host me)
         Events : 0.2184174

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed
       3       8       49        3      active sync   /dev/sdd1

```

```

me@me:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[0] sdd1[3] sdb1[1]
      2197715712 blocks level 5, 64k chunk, algorithm 2 [4/3] [UU_U]
      
unused devices: <none>

```

Can anyone offer some advice to get the drive back into the array (A rebuild of the array is fine)... I actually would like to check this drive before putting it back into the array (wiping it).  So assume I want to put this drive back in as a NEW drive.

---

### Post by fjgaude on 2009-10-18
Well, I can't say why the drive dropped out of the array.

You zero the superblock of the drive and then add it back in... it will then auto re-sync itself using all four drives.

First, fault the drive, then remove it:

```
sudo mdadm /dev/md0 -f /dev/sdc1

sudo mdadm /dev/md0 -r /dev/sdc1

sudo mdadm --zero-superblock /dev/sdc1

sudo mdadm --manage -a /dev/md0 /dev/sdc1
```

That should do it.

---

### Post by citium on 2009-10-18
When one of my drive is pop out after a restart.
I just "sudo mdadm --manage --re-add /dev/md0 /dev/sdc1"
and it just resync

---

### Post by fjgaude on 2009-10-19
> **citium said:**
> When one of my drive is pop out after a restart.
I just "sudo mdadm --manage --re-add /dev/md0 /dev/sdc1"
and it just resync

That works if the added drive is a good one... we think the drive is not good.

---

### Post by zackiv31 on 2009-10-20
Turns out the drive I had was bad, lots of reallocated sectors so I sent it in for RMA... I should be getting my new drive soon.

So if I'm adding a new drive, what would be the exact command?

(Thanks for the other commmands, those will come in handy down the line!)

---

### Post by fjgaude on 2009-10-21
Exact command, can't say. You array is still set to be four drives I would think that you would make the filesystem on your new drive the same size and type as the others, using **gparted** or the like. Then simply add the new drive in:

```
sudo mdadm /dev/md0 -a /dev/sdc1
```

It should start it sync adding the new drive. You can watch the process with:

```
sudo watch cat /proc/mdstat
```

Let us know how things go. Thanks!

---

### Post by zackiv31 on 2009-11-03
Finally got my drive, and finally got to use the above commands to get my raid back in order.

Gonna let it resync on this drive, then test it for bad sectors/problems... and actually back it all up and recreate it with an ext4 system instead :)

Thanks for the help!

---

### Post by fjgaude on 2009-11-04
Pray, do tell how the ext4 works for you...

Thanks!

---

### Post by zackiv31 on 2009-11-04
Well in 9.04 I had corruption issues... but im willing to give it a try once again...

can I just format my mdadm or do I need to recreate the whole array?

```

mkfs -t ext4 /dev/md0

```

Will re-creating the array from scratch yield better performance then the above command?  I never understood why I have to create a partition on each drive, set the boot flags, and then create the array... because after, it seems I still have to format the drives anyway and pick my filesystem...

Why do people recommend creating the partitions first with gparted or the like, and then create the array which seems to wipe them anyway?

Also, do I need to create the partitions or can I just create the array using the devices themselves (sda,sdb,sdc,sdd) instead of (sda1,sdb1,sdc1,sdd1)?

---

### Post by fjgaude on 2009-11-04
You might try formatting the complete array without going through a complete --create as usual.

I've always used one partition for the whole drive... that's the way I learned. Try it your way and see what happens.

Let me know how things go.

---

### Post by zackiv31 on 2009-11-04
No I don't think I'm explaining it well...

Say you have 4 unformatted drives you want to put into a new raid 5... do u just create the raid on the devices themselves (sda,sdb,sdc,sdd)?

Or do you create partitions (sda1,sdb1,sdc1,sdd1) and then feed those into mdadm --create ?

---

### Post by fjgaude on 2009-11-05
Well, many have done it both ways. I can't remember but it is said that creating a partition for each drive is a better way. So, I recommend:

"create partitions (sda1,sdb1,sdc1,sdd1) and then feed those into mdadm --create"

Yes... doesn't take long using gparted or cfdisk, both of which I use.

---

### Post by zackiv31 on 2009-11-07
Got my ext4 raid 5 building again... cat /proc/mdstat is showing speeds of 24904K/sec.  Should be built in a day... ran a hang checking script from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824) and no hang... I'm comfortable with ext4 and will be moving all my systems to this filesystem.

---

### Post by fjgaude on 2009-11-07
Okay, but that build speed of 25 MB/sec seems a little slow... I remember speeds of 50-70 MB/sec on my last ---create. So be it! Trust all works out for you.

---

### Post by zackiv31 on 2009-11-07
7200rpm seagate 750gigs in raid 5... why are ur speeds so much better?

Did I do something wrong?

---

### Post by fjgaude on 2009-11-08
Really don't know... could be the size of the drives... mine are 320 GB, four in raid5.

My box is fast, very fast:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz) 2/26/08, fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates

```
sudo hdparm -tT /dev/md32
 Timing cached reads:   18154 MB in  2.00 seconds = 9090.26 MB/sec
 Timing buffered disk reads:  616 MB in  3.01 seconds = 204.93 MB/sec
```

After you array is built, see what you get from the above command.

---

### Post by zackiv31 on 2009-11-08
I have onboard RAID, silicon Image on an Asus A8N... I have a feeling its because of the controller.

```

me@me:~$ sudo hdparm -tT /dev/md0 
/dev/md0:
 Timing cached reads:   1468 MB in  2.00 seconds = 734.06 MB/sec
 Timing buffered disk reads:  272 MB in  3.01 seconds =  90.38 MB/sec

```

I do an rsync of a 4.4gb file from the raid 5 to my raid 0 10k pair and I get 42.55MB/s.

EDIT:

Did an a timed copy of a 2.2gb file from the raid5 to my raid 0 and resulted in the following:

```

real	0m23.412s
user	0m0.030s
sys	0m15.290s

```

Is that system time what is killing my copies?  What's the holdup?  Got an Athlon X2 4800+ w/ 2GB ram.

---

### Post by fjgaude on 2009-11-08
Likely the **dmraid** is another layer of software... can't say for sure. CPU and memory would seem to be fast enough.

I use **mdadm** for my raid5.

---

### Post by zackiv31 on 2009-11-08
It seems to be in the writing... if I do an sfv check on some files on that raid, I get 91MB/sec... so it's somewhere in the transferring of those files off of/onto the drive... oh well, I guess there's not much I can do :-/

---

### Post by fjgaude on 2009-11-08
Really, with drives like you have you should be at least in the 180 MB/sec read range.

But like you say, what can you do? <smile>

---

### Post by zackiv31 on 2009-11-08
It kinda leaves me to believe that something is wrong with my machine... My 10k Raid 0 is only getting 112MB/sec... but then again, I thought I remember benchmarks for my setup at around that level.  In Raid5, shouldn't performance be lower then that of a single drive? (Do you have different performance on a single drive?)

---

### Post by fjgaude on 2009-11-08
Well, my single-drive performance is 70 MB/sec read. With raid5 you should get read speed of three drives combined in your case. Remember raid5 is similar to raid0, with stripping, but has the extra overhead of parity calucations. But with fast, fast CPUs these days that extra overhead doesn't hurt anything. So with four of my drives I should get 210 MB/sec, and I'm close.

What might be an issue is the SATA drive controller bus. If it is just PCI then that's your answer. I have PCI-E. The former is only good for about 120 MB/sec; the latter, 500.

---

### Post by zackiv31 on 2009-11-08
You might be on to something there... although I'll probably have to look at the specs for the chipset, because the specs for my motherboard aren't revealing much (beyond that I have PCI express and regular PCI)

[http://www.pcper.com/article.php?aid=98&type=expert](http://www.pcper.com/article.php?aid=98&type=expert)

Might be time for an upgrade afterall...


EDIT: Might be some confirmation here:

[http://www.tomshardware.com/forum/169596-28-sata-sata](http://www.tomshardware.com/forum/169596-28-sata-sata)

> 
Look at page 28 where it details what SATA chip this board uses.
"As a manufacturing option, the board provides a Silicon Image Sil 3114 Serial ATA (SATA)
controller and four connectors (that support one device per connector) for SATA devices. These connectors are in addition to the four SATA connectors of the ICH7-R/ICH7-DH SATA interface.
The Sil 3114 controller uses the PCI bus for data transfer and provides a maximum data transfer rate of up to 1.5 Gbits/sec."



EDIT2: Chipset info:

[http://www.siliconimage.com/iplicensing/product.aspx?pid=28](http://www.siliconimage.com/iplicensing/product.aspx?pid=28)

That seems like you're correct?

---

### Post by fjgaude on 2009-11-08
Yep. So now what?

---

### Post by zackiv31 on 2009-11-08
I buy a new machine?  lol... Kinda disappointed in the speed on them, but I'm mostly working with a NAS that tops out at 30MB/sec so I think I'll be keeping this machine for now.  I could shell out ~$100 for a "real" PCI E card (even for my main OS which would probably speed it up 2fold), but at that point I should just shell out for a new motherboard/processor/memory.

I don't *need* your types of speeds, but down the line I know I'll be upgrading to a monster machine at some point... just not right now... I spent a good chunk of change on this machine 4 years ago, its approaching its end of life... :(

---

### Post by fjgaude on 2009-11-09
Sounds good to me... speed is not everything... those who live by it usually die by it. <smile>

---

