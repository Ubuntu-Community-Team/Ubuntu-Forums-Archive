---
title: "mdadm RAID5 File Server Upgrade"
date: 2009-03-19
forum: Server Platforms
---

### Post by obscure_detour on 2009-03-19
I'm in somewhat of a dilemma and am hoping for some feedback.  This file server does nothing but minimal personal FTP traffic and serve files via samba on a gigabit network with about 3-8 users.  Under heavy load, I'd say 2-3 people streaming HD content and another 1-3 streaming compressed audio (MP3).  And via script it might be extracting large archived files at any given time.

**Current Hardware:**
[I]AMD Athlon X2 4400+ (2.2GHz)
2GB DDR2 800MHz
3x 750GB (RAID5)
Ubuntu 8.04 Server[/I]

**Future Hardware:**
[I]AMD Phenom II X3 720 (2.8GHz)
4GB DDR2 1066
3x 750GB + 1.5TB (RAID5)[/I]

Under heavy load CPU utilization would be 100% on both cores and read/write speeds start to crawl.  Most of the time it can handle the load, but sometimes it does effect the end users.

I assume adding a 1.5TB drive to the RAID5 array would work fine since Software RAID doesn't have the limitations of needing the same capacity drives.  Do I have this right?  The grow would work?

My next question is this, would I see a significant improvement in my RAID5 array performance wise?  Read/Write, etc.  Oh I did leave out my chipset info.  I can't remember which chipset I have in my server currently, I just know it's a really old AM2, which I blame a lot on my performance, not just my 4400 X2.  I know the new AM3 chipset will improve things greatly, not just the Phenom II.  

Next dilemma is whether going x64 or x86.  Since I will have 4GB of RAM now, I know using x64 would benefit that.  I've read countless threads/articles detailing the pros and cons.  I don't need flash, codecs, etc on this machine.  It would seem x64 would be the route to go given it doesn't effect mdadm, samba, etc...  I've also thought theoretically that x86-64 would speed the array up, give the fact the kernel is optimized for 64-bit.  That makes sense right?

I've also heard only great things about Intrepid 8.10, I've heard samba speeds have been improved and other things too.  Is it stable enough for a server?  I know LTS is meant for server due to the long term support, but I guess would you all recommend 8.10 on a new server build?  I have had no issues with Hardy except for this dumb [bug here]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/269651").  It doesn't effect my server at all except I see a bug report every few weeks.  Intrepid apparently has a fix for this bug.

Whew!  I'm sorry this is incredibly long.  Here's some more information you might need.  Since my server build about 8-9 months ago, I've had no issues and am still loving my decision to go the mdadm RAID route.  As you can see below my array is way too full!  Thanks in advance for any feedback you might have.

```
jms@server:~$ sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   2062 MB in  2.00 seconds = 1031.74 MB/sec
 Timing buffered disk reads:  516 MB in  3.00 seconds = 171.79 MB/sec
```

```
jms@server:~$ vmstat 2 5
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 1  0  39544  51952  51040 1335612    0    0     3     4    5    2  2  0 97  1
 0  1  39544  51876  51040 1335624    0    0    10     0  209  200  1  0 99  0
 0  0  39544  51584  51040 1335908    0    0   132     0  262  228  1  0 99  0
 0  0  39544  51584  51048 1335908    0    0     0    36  239  212  1  1 99  0
 0  0  39544  51276  51048 1336224    0    0   158     0  263  234  0  0 98  1

```

```
root@server:~$ mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 20 21:24:08 2008
     Raid Level : raid5
     Array Size : 1465143808 (1397.27 GiB 1500.31 GB)
  Used Dev Size : 732571904 (698.64 GiB 750.15 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar 19 14:09:47 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 3460b99b:373d05ed:b33a6fc1:0129fa20
         Events : 0.54

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1

```

---

### Post by obscure_detour on 2009-03-20
No suggestions or feedback?

Nobody can give any experience on increasing write/read performance in RAID 5 using mdadm?

Thanks.

---

### Post by fjgaude on 2009-03-21
Removed partial duplicate.

---

### Post by fjgaude on 2009-03-21
Re: mdadm RAID5 File Server Upgrade
Using modern controllers, e.g., PCI-E, the read thru-put of raid5 is n-1 times that of one drive. So, adding one more drive should increase your read speed to 250MB/sec.

With software **mdadm** all drives will end up being lowered to the smallest one. So, if you have 750MB units now, it does no good to add one that is 2TB, for it will be added as a 750MB.

I've not seen any difference between 8.04 and 8.10, although I don't use the server versions of either. I would think 8.10 will do you just fine.

With the kind of traffic you mention, I/O bottlenecks are common. SCSI drives would work better, but I know... expensive. For home use what you are doing will show some slight improvement... faster Intel CPUs would show more flash. <smile>

Here's mine with old, slower drives than yours:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

I'm a graphic designer and thru-put, reliability means everything to me. Notice my signature. I use three backups, one online, another near-line, and finally, one off-line, using Grsync and Unison.

---

### Post by obscure_detour on 2009-03-21
fjgaude, thank you for your feedback.  I honestly think the main issue is my motherboard and the old AM2 chipset.  I think anything modern Intel P35 and newer or any AM2+/AM3 would seriously help the read speeds.  I know I don't have a awesome cpu in there, but I'm seriously limited by the bus of the old AM2 chipset.

So my best bet would be to just get another 750GB drive?  Since adding a 1.5TB would render half of it unused?

I guess my real question is how much does the FSB, and amount of RAM effect the RAID performance?  I'm guessing quite a bit.

Based on [Wiki]("http://en.wikipedia.org/wiki/HyperTransport"), going from HyperTransport 1.0 (AM2) to HT 3.0 (AM3), bandwidth would be quadrupled.

---

### Post by fjgaude on 2009-03-21
Well, bandwidth is more about video and not disk I/O... when we talk about streaming huge files down Gigabit links we are dealing with lots of disk I/O working from many parts of the drives. That's where SCSI comes into play with their quicker access times. But all I can say is try and see.

Yes, go with an additional 750GB drive... and study up on how to grow the array. And by all means go with a 64-bit install of the OS. That way you will get close to 4GB in RAM, not 3.2GB. Yes, the more stuff that goes into cache RAM the faster everything is. <smile>

---

