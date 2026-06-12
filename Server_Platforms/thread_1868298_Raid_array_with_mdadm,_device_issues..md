---
title: "Raid array with mdadm, device issues."
date: 2011-10-24
forum: Server Platforms
---

### Post by halitus87 on 2011-10-24
Hi all. 

I am new to the forums, and linux really. Sorry if I have formatted it wrong. I have tried to lay out my issues clearly. Let me know if I should change this post some how. I have looked at a number of posts non of which seam to help.

I am trying to build an array on an ubuntu server (11.10) box, and I cant get it going. The system is running fine from the USB. I have disabled swap and enabled noatime.

my issue is that during a mdadm create it cant access one drive. Its down hill from there :(


Ill step through what I'm trying to do and what Ive done here:

_[MetaGoal]_ Build a NAS running an array and a few other services using a miniIXT board booting from a usb stick.

_[Goal]_ Create an array from 3 x2TB drives using mdadm.

_[Hardware] _
mobo: asus at5NM10t-I
boot drive: 4 gig usb stick (I installed ubuntu server on it via vmware in windows)
drives: 3 x 2TB seagate green drives
Memory: 4GB DDR3 running at 800 due to the miniITX board

_[What I have tried]_
i have sd[abc] for drives to go into the array. sdd is what the mobo enumerates the usb as.

becuase I had a half build degraded array on the drives I used dd to zero the first 100ish megs and the last 400ish. Now I should have no partitions on the drive.

**setup partitions:**

```
sudo fdisk /dev/sda
```

it warns me about the sector sizes. I tried changing it but my partitions came out small. They are 512 but the physical sectors are 4096.

I then press the following:
p , no partitions show up.
n,p,enter,enter,enter to make a primary parition with the default values.
t,fd,enter to change the type to linux raid auto.
w to write changes.

this gives the following:
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb63d1983

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  3907029167  1953513560   fd  Linux raid autodetect


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa11ecf56

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect


Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9a2eadde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect

sudo fdisk -l|grep raid
/dev/sda1            2048  3907029167  1953513560   fd  Linux raid autodetect
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect


```

So they seam ok.

**Setting up mdadm:**

I did an apt-get install mdadm and that installed ok.

now i tried to create the array with the following
```
sudo mdadm --create /dev/md0 --verbose --chunk=64  --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
```

This is where my issues arise.It spits out this:

```
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 1953512384K
mdadm: Defaulting to version 1.2 metadata
mdadm: ADD_NEW_DISK for /dev/sda1 failed: Device or resource busy

```

All the posts on the web point towards dmraid grabing the disk. I dont have dmraid on this system. ps aux|grep sda1 shows nothing interesting. Neither does lsof -l|grep sda.

mdstat gives this:

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[1] sda1[0]
      3907024768 blocks super 1.2 level 5, 64k chunk, algorithm 2 [3/2] [UU_]

unused devices: <none>

```

It seams that sda was added after all along with sdb. But where is sdc?

examining sda b and c gives the following (with their specific UUIDs):
```
 sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 9b8aa7d7:778bf218:2f7b3bc2:428676aa
           Name : Ix:0  (local to host Ix)
  Creation Time : Mon Oct 24 20:04:47 2011
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 3907025072 (1863.01 GiB 2000.40 GB)
     Array Size : 7814049536 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 3907024768 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 26c51ba8:2a466501:88f8681b:bc5dc54c

    Update Time : Mon Oct 24 20:04:47 2011
       Checksum : b76d56c3 - correct
         Events : 0

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AA. ('A' == active, '.' == missing)

```

details on md0 give:
```
sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Mon Oct 24 20:04:47 2011
     Raid Level : raid5
     Array Size : 3907024768 (3726.03 GiB 4000.79 GB)
  Used Dev Size : 1953512384 (1863.01 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Oct 24 20:04:47 2011
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           Name : Ix:0  (local to host Ix)
           UUID : 9b8aa7d7:778bf218:2f7b3bc2:428676aa
         Events : 0

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       0        0        2      removed

```


So now I am really lost. This happens every time I have tried to make this numerous times now.Any ideas?

_[Other things to note]_

My mobo has two sata controllers one built in to... something. The other is a jmicron chip i believe. Each has 2 ports. So for 3 drives i have one on one and two on the other. 

The jmicro controller can be set to IDE or disabled in the bios. Where as the built in controller has IDE/AHCI and the IDE setting can be set to compatibility or enhanced.

currently i have jmicro set to ide, and the built in one to ide-compatible.


_[plea for help]_
Please help, I have sat here for days now hitting my head against it. Any info you need just let me know (you might have to tell me how to get it though as I am new to linux)

Thank you very much.

Halitus

---

### Post by rubylaser on 2011-10-24
Sounds like you're not have a fun time so far :)  Welcome to the forums, and let me see if I can't get you back on the right track.  The first thing, you'll want to do is stop your running array.

```
sudo -i
```
```
mdadm --stop /dev/md0
```

Then zero the superblocks on your drives to make sure they're free of any mdadm cruft.
```
mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdc1
```

It would be nice to know the model # of your Seagate drives to see if they are in fact Advanced Format drives.

Finally, you'll want to clear out your mdadm.conf
```
 > /etc/mdadm/mdadm.conf
```

Now, you shouldn't have an array running and be ready to setup a new one...
```
mdadm --create /dev/md0 --verbose --chunk=64  --level=5 --raid-devices=3 /dev/sd[abc]1
```

Let the array finish syncing...
```
watch cat /proc/mdstat
```

Now that we have set up the array, we need to edit the mdadm configuration so it knows how to reassemble it when the system boots.

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Add a filesystem to your array...
```
mkfs.ext4 -b 4096 -E stride=16,stripe-width=32 /dev/md0
```

Set the reserved space to 0%
```
tune2fs -m 0 /dev/md0
```

Create a mount point.
```
mkdir /storage
```

And add it to your fstab...
```
nano /etc/fstab
```

and paste...
```
/dev/md0	/storage	    ext4	defaults	0	0
```

mount it
```
mount -a
```

You should now have a 3 disk RAID5 array that will survive reboots and be mounted on /storage.

---

### Post by darkod on 2011-10-24
> **rubylaser said:**
> You should now have a 5 disk array that will survive reboots and be mounted on /storage.

Sorry to jump in, but you mean 3 disk array RAID5, right? Just to make it clear, because I am preparing/investigating for RAID too and it got me confused.

---

### Post by rubylaser on 2011-10-24
Yes, I mean 3 disk, sorry, I had RAID5 on my mind.  I've edited my original post to remove confusion :)

---

### Post by halitus87 on 2011-10-24
Hi RubyLaser

Thanks for the help.

I tryed the first few commands up till creating the array.
Then i got the same issue as before.

```
 mdadm --create /dev/md0 --verbose --chunk=64  --level=5 --raid-devices=3 /dev/sd[abc]1
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: size set to 1953512384K
mdadm: Defaulting to version 1.2 metadata
mdadm: ADD_NEW_DISK for /dev/sda1 failed: Device or resource busy

```
which gives this...
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sda1[0](S)
      1953512536 blocks super 1.2

unused devices: <none>

```

as for the HDD  they are Seagate barracuda Green 5900 2TB,64MB, ST2000DL003
hdpram gives the following...
```
 sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
        Model Number:       ST2000DL003-9VT166
        Serial Number:      5YD5PWTA
        Firmware Revision:  CC3C
        Transport:          Serial, SATA Rev 3.0
Standards:
        Used: unknown (minor revision code 0x0029)
        Supported: 8 7 6 5
        Likely used: 8
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  268435455
        LBA48  user addressable sectors: 3907029168
        Logical  Sector size:                   512 bytes
        Physical Sector size:                  4096 bytes
        Logical Sector-0 offset:                  0 bytes
        device size with M = 1024*1024:     1907729 MBytes
        device size with M = 1000*1000:     2000398 MBytes (2000 GB)
        cache/buffer size  = unknown
        Nominal Media Rotation Rate: 5900
Capabilities:
        LBA, IORDY(can be disabled)
        Queue depth: 32
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 16
        Recommended acoustic management value: 254, current value: 0
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
                Security Mode feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    DOWNLOAD_MICROCODE
                SET_MAX security extension
           *    Automatic Acoustic Management feature set
           *    48-bit Address feature set
           *    Device Configuration Overlay feature set
           *    Mandatory FLUSH_CACHE
           *    FLUSH_CACHE_EXT
           *    SMART error logging
           *    SMART self-test
           *    General Purpose Logging feature set
           *    WRITE_{DMA|MULTIPLE}_FUA_EXT
           *    64-bit World wide name
                Write-Read-Verify feature set
           *    WRITE_UNCORRECTABLE_EXT command
           *    {READ,WRITE}_DMA_EXT_GPL commands
           *    Segmented DOWNLOAD_MICROCODE
           *    Gen1 signaling speed (1.5Gb/s)
           *    Gen2 signaling speed (3.0Gb/s)
           *    Gen3 signaling speed (6.0Gb/s)
           *    Native Command Queueing (NCQ)
           *    Phy event counters
           *    unknown 76[15]
                Device-initiated interface power management
           *    Software settings preservation
           *    SMART Command Transport (SCT) feature set
           *    SCT Long Sector Access (AC1)
           *    SCT LBA Segment Access (AC2)
           *    SCT Features Control (AC4)
           *    SCT Data Tables (AC5)
                unknown 206[7]
                unknown 206[12] (vendor specific)
                unknown 206[13] (vendor specific)
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
                supported: enhanced erase
        326min for SECURITY ERASE UNIT. 326min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c50045a7e262
        NAA             : 5
        IEEE OUI        : 000c50
        Unique ID       : 045a7e262
Checksum: correct

```

Sorry that was kinda long. Im not sure what was important or not so I gave it all.

Also weird things happened last night. I deleted everything from mdadm.conf I deleted all the partitions and stopped all the arrays.

then as i was re making the partitions I saw on my other monitor something popup and say something about an array and mdadm. This was after i had set two partitions. so i checked mdstat and sure enough it has created a raid 5 array on md127 with those two partitions. It also said one was missing [UU_]. I then added the last partitions to the array using --add and it started to resync (even though it should have been clean). I stopped this because I didn't create it and I don't know what was happening. 

Could there be an issue that my drives dont like being added all at once? I could add them one at a time i guess?

thanks again for any help

---

### Post by halitus87 on 2011-10-26
Update:

I have tried using gdisk instead of fdisk and started the partitions at block 2048 and ended them at a multiple of 8 also.

Same issue.

Another thought occurred to me after reading some ones web article/ blog post on their mdadm raid experiences.

[http://zargony.com/2008/03/23/assembling-a-partitionable-software-raid-with-mdadm-device-or-resource-busy]("http://zargony.com/2008/03/23/assembling-a-partitionable-software-raid-with-mdadm-device-or-resource-busy")

Could the kernel be trying to find swap space on one of my drives? keeping in mind i am booting from usb with no swap partition and as far as i know no swap file.

thanks again for any help, I am still beating my head against my case.

Halitus

---

### Post by darkod on 2011-10-27
Since all else failed, few ideas:

1. How about booting with the desktop version in live mode, and using Gparted to create and format the partitions for raid. Then try the mdadm commands from the server booted.

2. If this is still in early phase, how about reinstalling the server from scratch and creating the raid during the install. The install process offers you to create and configure the software raid.

---

### Post by halitus87 on 2011-10-27
Cheers, Ill give a live iso a go.

I dont have access to a cd/dvd drive for this pc so Ill do it with another usb stick. I may also try a non server version and not allow it to run a gui. (no idea how to do that yet but im not envisioning an issue)

As for using the installer. Is it possible to install server from one usb stick to another? Otherwise I dont know how to do it on this hardware. (perhaps that is an issue in it self)
I may also try freenas to prove that the hardware works. I dont think its a hardware fault with any drive, but just to be sure. I just dont want to run freenas as illd prefer to have a small Linux server to play with and set everything up my self, so I can learn about it and so I can have some hope of fixing things if they go wrong.

Cheers, Ill update when I have a chance to play with these.

---

### Post by darkod on 2011-10-27
I see no issue booting the server install from one stick and installing to another stick as destination. It's all just devices for the installer, I don't think it makes a difference.

---

### Post by halitus87 on 2011-11-05
Hi just an update. I am still working on this slowly.

Theres no problem installing from one usb to another it seams. Other than in the creation of the usb some times.  I found that i could make the array using a terminal in a live cd. But still no luck paritioning in the live session then building in the server install. 

Now I am trying to build a server using the regular kernel for 11.10 by doing an command line install. But this is proofing difficult as making an alternative installer usb stick doesnt really work. 

Im getting help on that in this thread:
[http://ubuntuforums.org/showthread.php?t=1872088](http://ubuntuforums.org/showthread.php?t=1872088)

Ill let you know if i can build the array once i get a command line version running.

Halitus

---

### Post by halitus87 on 2011-11-26
Ok no real luck as to figuring out how to make it do it as it should. But I am now up and running with a bit of a work around.

What worked for me:

1- Boot to a live session and parition and create the array there.

2- Use the raid builder in the partition creator during the server install.

I tried both and both seamed to work

Cheers
Halitus

---

