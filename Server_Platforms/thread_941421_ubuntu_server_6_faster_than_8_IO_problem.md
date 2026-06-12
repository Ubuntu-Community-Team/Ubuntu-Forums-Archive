---
title: "ubuntu server 6 faster than 8? I/O problem"
date: 2008-10-08
forum: Server Platforms
---

### Post by Astro6312 on 2008-10-08
All,

I have two servers with similar hardware, one has fast normal write speed on disk, the other one is extremely slow… up to 7x slower.

**FAST SERVER (VM3):)**
[INDENT]Supermicro: X7DB8+
CPU: Dual xeon quad core
Disk : ST3500630NS SATA 3GB/s connected to MB
OS: Ubuntu 6 server (2.6.15-52-server)
Test done : “time dd bs=1M count=1000 if=/dev/zero of=1000M.bin”
Result : 480MB/s

hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   13460 MB in  2.00 seconds = 6730.00 MB/sec
 Timing buffered disk reads:  314 MB in  3.00 seconds = 104.67 MB/sec
[/INDENT]

**SLOW SERVER (VM4):confused:**
[INDENT]Supermicro: X7QC3
CPU: Dual xeon quad core
Disk : WD1000FYPS SATA 3GB/s connected to MB
OS: Ubuntu 8 server (2.6.24-19-server)
Test done : “time dd bs=1M count=1000 if=/dev/zero of=1000M.bin”
Result : 69 MB/s

 hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   3878 MB in  2.00 seconds = 1939.36 MB/sec
 Timing buffered disk reads:  200 MB in  3.03 seconds =  66.09 MB/sec
[/INDENT]

CPU wait is much higher on the SLOW server.  Funny thing is that the "slow" server vm4 has better hardware, more recent purchase, and updated ubuntu 8 instead of 6.

I am running vmware on both and the slow server seems to slow to a crawl when we use disk I/O.

Any suggestion, comments?

Thanks,

---

### Post by Drezard on 2008-10-08
Try using Ubuntu 8 on the Vm3 computer. Just to narrow down.

Post what happens.

Daniel

---

### Post by Astro6312 on 2008-10-08
I am downloading the desktop edition of version 6.  I will boot the VM4 server with it and see if the disk access are faster than with the version 8.

There is days of work in those server, reboot with a live CD will be faster.

I will report back in a few hours...

Thanks,:)

---

### Post by Astro6312 on 2008-10-08
Goal of the test: Try ubuntu 6 on the slow server to see if disk I/O improves... :(

[INDENT]I was unable to start the live CD or rescue CD of ubuntu 6 on that server (VM4).  It does not work... So this test is no good.
[/INDENT]

I booted the live CD of ubuntu 8 and the live CD of fedora 9 on VM4, did some test and same result... SLOW... :(

I will try the live CD of ubuntu 8 on the fast server to see if the disk I/O are slower... This will be done after hours, so I will report back in a couple of days.

Any suggestions, comments?

---

### Post by smileypaul on 2008-10-08
Interesting you brought this up, although it could be hardware related, i have noticed a severe decrease in I/O performance on a server I have after upgrading from 6.06LTS to 8.04LTS .. 

I havent narrowed it down though, it could well likely be a hardware issue.

---

### Post by Krupski on 2008-10-08
> **Astro6312 said:**
> All,

I have two servers with similar hardware, one has fast normal write speed on disk, the other one is extremely slow… up to 7x slower.

**FAST SERVER (VM3):)**
[INDENT]Supermicro: X7DB8+
CPU: Dual xeon quad core
Disk : ST3500630NS SATA 3GB/s connected to MB
OS: Ubuntu 6 server (2.6.15-52-server)
Test done : “time dd bs=1M count=1000 if=/dev/zero of=1000M.bin”
Result : 480MB/s

hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   13460 MB in  2.00 seconds = 6730.00 MB/sec
 Timing buffered disk reads:  314 MB in  3.00 seconds = 104.67 MB/sec
[/INDENT]

**SLOW SERVER (VM4):confused:**
[INDENT]Supermicro: X7QC3
CPU: Dual xeon quad core
Disk : WD1000FYPS SATA 3GB/s connected to MB
OS: Ubuntu 8 server (2.6.24-19-server)
Test done : “time dd bs=1M count=1000 if=/dev/zero of=1000M.bin”
Result : 69 MB/s

 hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   3878 MB in  2.00 seconds = 1939.36 MB/sec
 Timing buffered disk reads:  200 MB in  3.03 seconds =  66.09 MB/sec
[/INDENT]

CPU wait is much higher on the SLOW server.  Funny thing is that the "slow" server vm4 has better hardware, more recent purchase, and updated ubuntu 8 instead of 6.

I am running vmware on both and the slow server seems to slow to a crawl when we use disk I/O.

Any suggestion, comments?

Thanks,

I'm going to follow this with great interest... since my hard drive speeds (with WDC 1TB drives!) are similar to your "slow" machine.

---

### Post by Astro6312 on 2008-10-09
I would like to discuss those lines from hdparm:

[INDENT]**FAST**
Timing cached reads: 13460 MB in 2.00 seconds = 6730.00 MB/sec
**SLOW**
Timing cached reads: 3878 MB in 2.00 seconds = 1939.36 MB/sec[/INDENT]

The difference is mostly felt there. This is 3.5 time faster reading from cache on the fast system.  

**So the question is:** 
[INDENT]What can affect cache reads which is memory reads?[/INDENT]

I also understand that hdparm is mostly for IDE drive and sdparm for SATA drives. My drives are SATA drives. But sdparm does not have the same timing gathering options.

One thing I see also is that the slowdown is felt not only on the SATA drives but on the RAID controller connected to the PCI bus.  It is a 3ware RAID 5 array.

So it seems that the common hardware between the SATA and PCI bus is the south bridge of the motherboard chipset.

Could there be a bug between some chipset and kernel version?

The fast system (VM3) is a supermicro X7DB8+ with 5000P chipset
The slow system (VM4) is a supermicro X7QC3 WITH intel 7300 chipset

I still need to boot the fast VM3 server with Ubuntu 8 live CD is see if I get the slow down.  I am scheduling this test tomorrow morning.

Thanks,

---

### Post by windependence on 2008-10-09
> **smileypaul said:**
> Interesting you brought this up, although it could be hardware related, i have noticed a severe decrease in I/O performance on a server I have after upgrading from 6.06LTS to 8.04LTS .. 

I havent narrowed it down though, it could well likely be a hardware issue.

This is one reason people need to realize that the latest and greatest will certainly NOT always give you better performance in any area. Sometimes, certain kernel versions just like your hardware. Many times, a new version will be more bloated and actually slower than the old one especially with a GUI. Think Windoze Vista.

-Tim

---

### Post by Astro6312 on 2008-10-09
Ok here's some more tests on another server... Called VM2.  This one is older:
[INDENT]2 Xeon 3.4Ghz Hyperthread
8 Gig RAM
3ware: 9550SX-4LP
Supermicro: X6DH3-G2[/INDENT]

I booted from the ubuntu 8 live CD to compare the disk I/O with ubuntu 6 installed on the system

Here's the result on 3 disk.

/dev/sda is the RAID 5 array
/dev/sdb and sdc are SATA drives connected on the MB

[FONT="Fixedsys"]_________________Ubuntu 8 (liveCD)____Ubuntu 6 (Server)
hdparm -tT
sda cache read___991 MB/s_____________1956 MB/s   
sda buffer read__112 MB/s_______________95 MB/s

sdb cache read___983 MB/s_____________1896 MB/s   
sdb buffer read___57 MB/s_______________57 MB/s

sdc cache read____977 MB/s_____________1954 MB/s
sdc buffer read___57 MB/s_______________57 MB/s

DD 1GB write sda__53 MB/s______________221 MB/s[/FONT]

Sorry about the ___ I did not find a good way to format a table:confused:

So there is definitely something wrong with Ubuntu 8 compared with 6 on the same hardware.

Comments?

---

### Post by fjgaude on 2008-10-09
Well, glad to see someone interested in quickness, speed. I've begin to notice things that don't seem right with **hdparm** and drive thruputs. Here's two tests:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v: 4x raid5 Seagates:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec

```
---
4x raid5 **Samsungs**, CPU at 3.6GHz:
```
/dev/md32:
 Timing cached reads:   18182 MB in  2.00 seconds = 9103.61 MB/sec
 Timing buffered disk reads:  540 MB in  3.00 seconds = 179.75MB/sec
```

The Seagates measured with hdparm -tT at about 70MB/sec while the Samsungs at 107MB/sec.

Now in a four-drive raid5 array, **mdadm** software, I get the Seagates faster.

Doesn't make much sense, but then you think about the drive caching electronics and how each handles seeking, etc.

I do like the cached memory reads and why not, they are at 1066MHz, with a very fast dual-core CPU at 4GHz.

Please keep us informed with any results you come up with. Thanks!

---

### Post by volkswagner on 2008-10-19
Any progress folks?  I am interested in this.  I have performed an 8.04 server install on what I thought to be similar hardware (compared to my 6.06 server install)

6.06 running on pent2 400mhz, 384meg ram, AGP vid card, 8gig HD

8.04 running on celeron 500mhz 384meg ram, onboard video, 6gig HD

The 8.04 install went ok.  In fact both installs were via the appropriate "The perfect server"  on how to forge.  I noticed a lot of lag when running ssh via a remote machine.  Web pages also seemed to be slow on this machine.

I did not verify hard disk specs, I assumed they were similar, since they were of similar vintage.

Anyway the 8.04 install is painfully slow.  Is there anything I can do to contribute to testing?  I too would like to know if 6.06 is faster.

Do you think there is something wrong with my 8.04 install or hardware?  Is it worth investigating?

Sorry if this is not on topic.

---

### Post by Astro6312 on 2008-10-19
> anything I can do to contribute to testing? I too would like to know if 6.06 is faster

Sure you can run hdparm and dd tests (see previous post) on both system and post the result.

Myself, I am quite sure there is something different with 8.04.  Seems like the CPUwait is way higher when doing disk I/O compared with 6.06.

Every low level test I do show 8.04 slower than 6.06, but high level test are faster!  So I compare a hdparm and DD test (low level) with file copy from a PC on the network to a VM guest running on a VM host.

The performance is so bad, that I will probably switch to using VMware ESXi which has it's own operating system.

---

### Post by Astro6312 on 2008-10-20
Some saw some performance drop between ubuntu 6 and 7...

[http://ubuntuforums.org/archive/index.php/t-390247.html](http://ubuntuforums.org/archive/index.php/t-390247.html)

This maybe related

---

### Post by volkswagner on 2008-10-20
My plan for testing is to take the slow machine, dual boot two clean installs of 6.06 and 8.04.  I plan to use two exact partition sizes (2.5gig ea.).  

Shall I use 8.04 or 8.04.1?  I have 8.04 burned but not 8.04.1.
Shall I do LAMP installs or just base with openssh?
EXT2 or EXT3 format?  I always use EXT3.
Any other suggestions?

I will attempt in the next couple days.

---

### Post by Astro6312 on 2008-10-20
I would go with the latest 8.x and 6.x fully patched.  We don't want to test with an unpatched system.

I always use also EXT3.

Lamp or not does not matter much, as long as the test is ran with a CPU as idle as possible.

If also you could run a real world test, like using samba and copying files from a network PC and measuring write-read speed.

I have found that "real" work is difference than benchmark like DD or hdparm.

Thanks,

---

### Post by volkswagner on 2008-10-20
OK, downloading 8.10 Beta server now.

---

### Post by volkswagner on 2008-10-24
> **Astro6312 said:**
> I would go with the latest 8.x and 6.x fully patched.  We don't want to test with an unpatched system.

How do I verify I am fully patched?  I installed 6.06 server, installed openssh-server, performed update and upgrade.  I restarted and performed update and dist-upgrade to include image server.  Rebooted for new kernel, right? What else?
  

I am currently installing 8.10 Beta.  I think I may have made a mistake.  I am used to multi-booting with desktop versions.  They usually include grub auto install to the first partition.

I just have hda1 for 6.06, hda2 for 8.10, and hda3 for swap.  I set hda1 flag to boot.  Should I have made a /boot partition?  Will I be able to install grub to hda1 and find both OS installs?

EDIT: Just got to the Grub install.  I should have no problem.  Please ignore the above.

Sorry for going way of topic.  I will start a new thread if need be.

Peace,

Eric

---

### Post by StickyStyle on 2008-10-24
I'll chime in with similar results.  I just started evaluating 8.04 over 6.06 for a VMware server project and noticed that it was performing horribly against a physically identical 6.06 server.

Both Dell PowerEdge 1850's with 4GB RAM, PERC RAID with two 15K RPM U320 SCSI drives in RAID1.

==8.04 Box==
```

administrator@vmx1:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1816 MB in  2.00 seconds = 908.36 MB/sec
 Timing buffered disk reads:  238 MB in  3.02 seconds =  78.91 MB/sec

administrator@vmx1:~$ time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 21.2264 s, 49.4 MB/s

real	0m21.943s
user	0m0.000s
sys	0m4.630s

administrator@vmx1:~$ uname -a
Linux vmx1 2.6.24-21-server #1 SMP Mon Aug 25 18:06:43 UTC 2008 i686 GNU/Linux


```

==6.06 Box==
```

root@NAS1:~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   3776 MB in  2.00 seconds = 1888.00 MB/sec
 Timing buffered disk reads:  270 MB in  3.00 seconds =  90.00 MB/sec


root@NAS1:/root# time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 1.92275 seconds, 545 MB/s

real	0m2.621s
user	0m0.000s
sys	0m1.890s

rparrish@NAS1:~$ uname -a
Linux NAS1 2.6.15-52-server #1 SMP Fri Sep 5 15:20:44 UTC 2008 i686 GNU/Linux


```

---

### Post by fjgaude on 2008-10-25
Here's what I get on an Ubuntu 8.04, 3.6GHz Intel E8400 machine. First with a single, fast SATA drive:

```
frank@sunshine:~$ time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 15.0521 s, **69.7 MB/s**

real	0m15.053s
user	0m0.000s
sys	0m1.216s

frank@sunshine:~$ sudo hdparm -tT /dev/sda1:
/dev/sda1:
 Timing cached reads:   12750 MB in  2.00 seconds = 6379.28 MB/sec
 Timing buffered disk reads:  188 MB in  3.02 seconds =  **62.15 MB/sec**
```

Then with a four-drive SATA mdadm software raid5 array:

```
frank@sunshine:/home/raid$ time dd bs=1M count=1000 if=/dev/zero of=1000M.bin
1000+0 records in
1000+0 records out
1048576000 bytes (1.0 GB) copied, 9.43075 s, **111 MB/s**

real	0m9.570s
user	0m0.000s
sys	0m1.408s

frank@sunshine:/home/raid$ sudo hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   15750 MB in  2.00 seconds = 7882.54 MB/sec
 Timing buffered disk reads:  526 MB in  3.01 seconds = **174.96** MB/sec
```

I do believe the testing leaves something to be desired from a scientific point of view.

---

### Post by volkswagner on 2008-10-25
OK, I got some hdparm results.  I need to do my homework for dd. 


/dev/disk/by-uuid/f53dcd73-f939-4049-8179-740d1972b629:
 Timing cached reads:   190 MB in  2.01 seconds =  94.41 MB/sec
 Timing buffered disk reads:   40 MB in  3.03 seconds =  13.19 MB/sec


Hdparm on 6.60 server

/dev/disk/by-uuid/f53dcd73-f939-4049-8179-740d1972b629:
 Timing cached reads:   456 MB in  2.01 seconds = 226.87 MB/sec
 Timing buffered disk reads:   40 MB in  3.03 seconds =  13.20 MB/sec

What I notice is the lag.  When using the terminal I often get lag while typing using 8.10 and 8.04.  I don't get any lag on 6.06.

---

### Post by fjgaude on 2008-10-26
Are you making these measurements when the system is heavily loaded? Those numbers seem very low.

---

### Post by volkswagner on 2008-10-26
> **fjgaude said:**
> Are you making these measurements when the system is heavily loaded? Those numbers seem very low.

If you are referring to my test, no.  These are clean installs on old hardware.  Only added service is openssh-server.  It is also on a 5400rpm disk.

Test Machine specs:

```
running on celeron 500mhz 384meg ram, onboard video, 6gig HD 5400rmp
```


Also on old hardware- 6.06-server, Pent2 400mhz, 384meg, sep vid card, 6gig HD 5400rpm, LAMP server running Postfix/courier/squirrelMail/ with very little user activity.

```

/dev/disk/by-uuid/dd97c503-a3c8-49c0-b9cc-922353cf7cee:
 Timing cached reads:   496 MB in  2.00 seconds = 248.00 MB/sec
 Timing buffered disk reads:   34 MB in  3.01 seconds =  11.30 MB/sec
```

---

### Post by StickyStyle on 2008-10-26
> **fjgaude said:**
> Are you making these measurements when the system is heavily loaded? Those numbers seem very low.

In my tests, no.  
The 8.04 machine was not yet in production and the guest operating systems where not running (server was testing to be a VMware box).  The 6.06 box is nothing but a file server and the readings where taken after hours when it was not in use by any clients.

Forgot to add that both of these boxes are dual 2.3GHz Xeons.

---

### Post by fjgaude on 2008-10-26
Well, one of you are on slow computers by modern standards. That 545MB/s showing from **dd** is amazing, but is it real?

I'm beginning to feel that **hdparm** is not tuned for 8.04 or 8.10, or the latter is different than hdparm figured when it was designed but works correctly for 6.06.

We will see a month or two after 8.10 is released and the bug fixes get into place.

---

### Post by volkswagner on 2008-10-26
I would like to know the reason for latency.  Why does 8.04/8.10 have delayed response from the keyboard.  When ssh'ing to each server, 6.06 has no latency yet the later releases have unexceptable delay.  Sometimes it is painfully slow, like throw a brick at the screen, frustratingly slow.  

How do I pin down the cause?

Personally I feel there is something more fundamental than disk I/O.

I am a newbie.  I am not sure how to properly diagnose the delay. 
 
If 8.04 is the new LTS and 6.06 has higher performance, how do I choose?

---

### Post by cariboo on 2008-10-27
Phoronix has done some testing, although it was between desktop vesion from 7.04 to 8.10, their conclusion was that there definitely is a slow down in newer versions. See the results here:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_bench_2008&num=1)

Jim

---

### Post by fjgaude on 2008-10-27
Very interesting... my subjective sense doesn't support these findings though I'm sure they are correct.

I seem to notice hard drive and raid performance fall after each release comes out, at least from testing using **dd** and **hdparm**.

But overall I guess we are happy with the overall way things are going, eh?

---

### Post by lewtwo on 2008-10-27
I had a similar problem with a supermicro dual opterron system. Drives writes just died at times. Could not figure it out. Moved the drives to different controlers, changed OS ... nothing was consistent. Then I found out that there were some WD drives floating round with lowlevel firmware problems. Turns out I had four of them. Sent 'em back to WD for replacements and no more problems.

---

### Post by fjgaude on 2008-10-27
Well, I had to go through six, count 'em, Seagates to get a good one. Now I'm okay with Samsung.

---

### Post by Astro6312 on 2008-10-28
Well this as become a big discussion... The conclusion definitely point to a problem with newer version of the kernel used in ubuntu 8 and other os (tried with FC9).

I did on the same hardware some test with DD.  So Writing a 1Gig:
Write speed: Ubuntu 6 vs 8 - 208 MB/s <> 24 MB/s
Read speed : Ubuntu 6 vs 8 - 344 MB/s <> 40 MB/s

One thing interesting that may point to the root cause is that looking at the drive LEDS, they where lit-up for about the SAME amount of time.  But on Ubuntu 6, the kernel gave me the prompt back much faster than ubuntu 8.

This is interesting in the light of another test I did.

On a test between two servers:
Server 1: Ubuntu 6 + VMware 2.x + 2003 guest 
Server 2: Ubuntu 8 + VMware 2.x + 2003 guest (faster, newer server)

I did a disk benchmark inside both VM guest with [BMX]("http://www.majorgeeks.com/download1800.html")... The result.

[IMG]http://infosilem.ca/simon/Forum_Ubuntu_post_perfo_28oct08.png[/IMG]

Look at the server load and time to complete... AMAZINGLY slow on Ubuntu 8.  The whole servers become un-responsive while the load is high like that. Not a problem with Ubuntu 6...

So according to this test on a real application like VMware, Ubuntu8 compared with Ubuntu 6 is unusable.  

I am planning to go back to Ubuntu 6 ASAP.

The problem is that I needed Ubuntu 8 to resolve issues with NFS on ubuntu 6 and I will need to manually load some 3ware drivers for more recent raid card.

Comments?

---

### Post by Astro6312 on 2008-10-29
I have entered a bug for this thread

[https://bugs.launchpad.net/ubuntu/+bug/290438](https://bugs.launchpad.net/ubuntu/+bug/290438)

---

### Post by Astro6312 on 2008-11-04
I installed and tested ubuntu 8.1 on the server where I had fast I/O on ubuntu 6 and slow I/O on ubuntu 8.04.

Everything is fast... probably faster than ubuntu 6.

It seems that the I/O problems are gone in ubuntu 8.1

This is good news.

The test I did is two RAID 5 controllers with 3 disk each. I used DD to write 1Gig file to each raid 5 at the same time and got around 200MB/s write speed.

Doing one test at a time, I got between 380MB/s up to 550MB/s.

---

### Post by Astro6312 on 2008-11-25
Ok here's the final conclusion of my tests...

I finally settled on this configuration.

1. Ubuntu 7
2. VMware 2.x
3. 2x RAID-5 Controller
4. Software RAID0 on 2 partitions on both RAID-5

I mount a VM guest disk on the RAID0.

This gives me a average of 165MB/s write and 380MB/s read on a 3GB file test from inside a VM guest, with a bearable load on the host.

Ubuntu 8.1 was giving very slow performance inside a VM guest.

Hope this will help someone out there, I spend many days finding the right balance of hardware and software that works well together.

Let me know if you have more questions, I watch this thread.

Thanks,

---

### Post by nroussi on 2008-12-05
Well since this thread is about benchmarking I am posting my problem too. I have it also on another thread ([http://ubuntuforums.org/showthread.php?t=1001858](http://ubuntuforums.org/showthread.php?t=1001858)), but there it start off with a different problem.

This is what I have:
/dev/sda PERC 5/e Controller for MD1000 14 Seagates 500GB in RAID5
/dev/sdb 3WARE 9650 SE 4 Seagates in RAID 5

/dev/sdb is for the OS, swap and boot
/dev/sda will be used only for data

I run the postmark benchmark which you can read at the above post. After reading this post I run hdparm and these are my results:

> nicolas@edubuntuS2:~$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   10298 MB in  2.00 seconds = 5153.34 MB/sec
 Timing buffered disk reads:  1064 MB in  3.00 seconds = 354.28 MB/sec
nicolas@edubuntuS2:~$ sudo hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   10358 MB in  2.00 seconds = 5183.34 MB/sec
 Timing buffered disk reads:  326 MB in  3.01 seconds = 108.47 MB/sec

nicolas@edubuntuS2:~$ uname -a
Linux edubuntuS2 2.6.24-21-generic #1 SMP Tue Oct 21 23:09:30 UTC 2008 x86_64 GNU/Linux


For sdb I have server grade seagates with 32MB cache and on sda I have regular OEMs with 16MB cache. Shouldn't sdb on the 3ware be faster than sda on the PERC?

---

### Post by fjgaude on 2008-12-05
Pretty hard for four drives in raid5 to be as fast as 14 also in raid5.

---

