---
title: "Help to set up raid 10 on ubutu 8.04 server LTS"
date: 2008-12-23
forum: Server Platforms
---

### Post by serverCrazy on 2008-12-23
hi, 

i am new to raid configuration and i want to set up a software raid 10 using ubuntu 8.04 server or maybe raid 1 over lvm (not sure).

I have 4 Hard drives of 1TB.

Any good link about it will help a lot, but please link me to the basics first, otherwise i will be confused and i want to know what i am doing from the begining,

thanks very much

---

### Post by speed32219 on 2008-12-23
Some good reading or understanding.

[http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10](http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10)

And multiple how to:
You choose

[http://linux-raid.osdl.org/index.php/RAID_setup](http://linux-raid.osdl.org/index.php/RAID_setup)
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

And Growing your Raid:
[http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)

---

### Post by albinootje on 2008-12-23
> **serverCrazy said:**
> hi, 

i am new to raid configuration and i want to set up a software raid 10 using ubuntu 8.04 server or maybe raid 1 over lvm (not sure).

I have 4 Hard drives of 1TB.

Any good link about it will help a lot, but please link me to the basics first, otherwise i will be confused and i want to know what i am doing from the begining,

thanks very much

I'm also interested in using software RAID10 myself.

I've been looking at the following links a few weeks ago :
[http://howtoforge.com/install-ubuntu-with-software-raid-10](http://howtoforge.com/install-ubuntu-with-software-raid-10)
[http://www.linuxtoday.com/high_performance/2008081403135OSSV](http://www.linuxtoday.com/high_performance/2008081403135OSSV)
[http://www.linuxtoday.com/it_management/2008082400435OSKNSV](http://www.linuxtoday.com/it_management/2008082400435OSKNSV)

(I've left the latter two links like that so that you can still read the comments from the readers at linuxtoday.com)

I've read that software RAID10 is still called "experimental" in the Linux kernel. Not sure what to think about that, I would like to know more details about that.

My experience so far is with using Debian in VirtualBox with 4 virtual disks.
I was reminded during the installation that the Debian installer does support software RAID 0,1 and 5, but not 10.
I fiddled a bit with having a separate partition as RAID10, and I left it like that for the moment.

HTH.

---

### Post by waster on 2009-03-22
be aware that each layer does different things to mess up the nice RAID stripes. particular caution with metadata clumping on one disk with LVM (I think there is an option to dodge this). make sure stride is used when create your ext2/3/4

[http://busybox.net/~aldot/mkfs_stride.html](http://busybox.net/~aldot/mkfs_stride.html)

(nb default block size in web page is not correct for me, at least)

this whole thing is a complicated mess - but for once, there is a huge performance hit, unlike most tweaks. four disks should read approximately four times faster than one disk, but without readahead and stripe optimisation, they can be SLOWER than a single disk. My Raid0 has higher throughput than my raid 10 right now. (ext/reiser on lvm on raid)

if you can skip the LVM step, you will have less to worry about, but sacrifice flexibility. if you are also encrypting a disk or partition, you will be going back 10 years in performance.

i'm waiting for a tool to at least advise on the settings needed in all the three+ layers to achieve harmony, or ideally for the partitioner to realise what's going on and sort it all out for you.

---

### Post by windependence on 2009-03-22
Obviously every case is different. RAID 5 will always give you better price/performance/disk space than RAID 10.

Time to rebuild a 4 disk Raid 10 is about 5 to 10 times faster than rebuilding a Raid 5.
Mainly due to the parity calculations but also depends on controller algorithms.

Every corporate setting where I have worked used RAID 5. One worldwide company had well over 1,000 servers using various OSs, all with RAID 5.

I don't see a reason to use 10 other than the "cool" factor.

-Tim

---

### Post by Brazilian Joe on 2009-04-02
> **windependence said:**
> Obviously every case is different. RAID 5 will always give you better price/performance/disk space than RAID 10.

...

-Tim

Almost true. RAID10 performance is better, as it does not do parity calculation. When it writes, RAID5 reads it back to check if it has been written correctly, this is safest but wastes performance (both KBps and I/O operations). RAID10 wastes space though, you get more of your storage with RAID5. 

Remember that big enough RAID setups require RAID 6 (4 1TB disks or more).

---

### Post by windependence on 2009-04-03
More spindles = better performance, therefore smaller drives and more of them is better in a RAID 5 setup.

I don't know what you mean by this:
> Remember that big enough RAID setups require RAID 6 (4 1TB disks or more).This setup could certainly be done in RAID 5, and with RAID 6 you lose two disks instead of one for parity.

-Tim

---

### Post by Brazilian Joe on 2009-04-03
> **windependence said:**
> More spindles = better performance, therefore smaller drives and more of them is better in a RAID 5 setup.

I don't know what you mean by this:
This setup could certainly be done in RAID 5, and with RAID 6 you lose two disks instead of one for parity.

-Tim

The case is that given a big enough RAID array, RAID 5 protection becomes nullified, because the probability  of a read error being raised during reconstruction approaches 1.
I have read this article (unfortunately I don't recall where), which is not very old (google is your friend), where the author explains that doing RAID with 1TB+ disks makes this statistical probability very significant.
So, if your RAID is big enough, double redundancy is a necessity, not a luxury, so one should consider RAID 6. Of course you lose one more disk, thus speed, but you get the necessary protection. 

If you are more on the performance side of things though, Linux Software RAID has the 'far' RAID 10 layout, where the data is disposed in a way that optimizes reading. With RAID 10 you should get more read performance than RAID5/6.

Usage patterns also tend to favor different RAID settings. RAID10 tends to favor database workloads, where RAID5 is best suited to file servers.

If you are on software RAID, there is yet aother item which comes into play: the disk controller. JMicron seems to be crap to access drives simultanoeusly, but Intel seems to be good. I'd stick with one of Intel/nVidia/AMD, depending on your cpu preference. if you can afford a true RAID controller, go for it.

If you are more after the performance than disk capacity, you can try half-stroking your disks. That's using only the 50% outer edge of the disk (the fastest part) for data. this way you reduce the arm movement of the disk, resulting in beter performance. you can reduce the disk used areas much as you want, even 10% or less, and you should see the improvement.

Depending on your filesystem of choice, you should also watch for proper flags to use during formatting. EXT3 for instance has the --stride option, to better distribute the filesystem metadata throughout the disks and avoid bottlenecks.

The best thing you can do is do your homework, don't take my words (or anyone else's) as the ultimate truth, but as advice, study the documentation, take your time and benchmark your own rig. Look at the numbers and make up your mind. 

Good luck!

---

