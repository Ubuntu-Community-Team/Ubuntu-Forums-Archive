---
title: "Comparative tests for very high-end PCs?"
date: 2010-06-02
forum: Server Platforms
---

### Post by Ulysses_ on 2010-06-02
Fifteen years ago buying a new computer was easy, magazines provided comparative tests of PCs for one's budget. Now typical magazine specs are not high enough for my needs:  

I need a PC that can duplicate a 5 gb file in less than 10 seconds.  

Where do I find comparative tests for PCs at this very high end?

---

### Post by Fully216 on 2010-06-02
The typical bottleneck of a computer is the front side bus.  Given your constraints, 5GB in 10 seconds means a bandwidth of roughly 512 MB/s.

Lets look at a basic Pentium 4 system as an example.  A 64-bit (8-byte) wide front side bus operating at a frequency of 100 MHz that performs 4 transfers per cycle has a bandwidth of 3200 MB/s.  Keep in mind that is the theoretical maximum, whereas must computer run at 70% that or lower for various reasons depending on system load, the particular operating system, and other reasons.

The number of transfers per clock cycle is dependent on the technology used. For example, GTL+ performs 1 transfer/cycle, EV6 2 transfers/cycle, and AGTL+ 4 transfers/cycle.

This bottleneck is becoming less true in recent years with the use of individual point-to-point connections in new system designs.  If you require this as your system minimum, then you will not be disappointed when new designs outperform your needs.

If you are doing a simple copy of data on a hard drive rather than manipulating data in memory, the speed of your hard will make a HUGE difference.  As of 2008, a typical 7200 rpm hard drive has a "disk-to-buffer" data transfer rate of about 70 MB/s, which is much slower than what the front side bus can handle in most cases, especially the one mentioned above.  The actual data rate will depend where the data is stored on the drive (inner track versus outer tracks).

A current widely used standard for the "buffer-to-computer" interface is 3.0 Gbit/s SATA, which can send about 300 MB/s from the buffer to the computer, and thus is still comfortably ahead of today's disk-to-buffer transfer rates.

In most cases, depending if you are writing data to a drive our simply using data in memory, will depend on if you get the data rate you desire.  For your needs, I would recommend a really fast hard drive if that bandwidth is for writing data.

---

### Post by Ulysses_ on 2010-06-02
Thanks, but where do I find comparative tests?

 Btw, it's reading and writing (duplicating) the file, therefore it's 1 GB/s.  I was looking at this SSD drive below for example.  But where's a comparative test of computers using this or similar drives?

 [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227499](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227499)

---

### Post by dragos2 on 2010-06-02
For such high disk transfers I would suggest a RAID array of SSD's like 6 x SSD in RAID 0, or
12 x SSD in RAID10 if you need fault tolerance and high speed.

Check reviews but I don't think the OCZ can copy a 1 Gb/s, at most 800 Mb/s, you need an array like I described before.

---

### Post by Ulysses_ on 2010-06-02
So it does not matter much what computer you put this on as long as the motherboard has a PCI-E x8 socket?  Maybe then I ought to go back to magazines for the computer for overall performance/price ratio, and simply add that SSD drive?  800 Mbytes/s is close enough.

---

### Post by dragos2 on 2010-06-02
> **Ulysses_ said:**
> So it does not matter much what computer you put this on as long as the motherboard has a PCI-E x8 socket?  Maybe then I ought to go back to magazines for the computer for overall performance/price ratio, and simply add that SSD drive?  800 Mbytes/s is close enough.

I am not an expert but a PCI-E x8 would do a maximum of 2 GB/s theoretically.
[http://en.wikipedia.org/wiki/List_of_device_bandwidths](http://en.wikipedia.org/wiki/List_of_device_bandwidths)

Besides the SSD's you will need to pay attention to the RAID card too and pick a top
one to cope with the load.

---

### Post by cascade9 on 2010-06-02
> **Ulysses_ said:**
> Thanks, but where do I find comparative tests?
 
 Btw, it's reading and writing (duplicating) the file, therefore it's 1 GB/s. I was looking at this SSD drive below for example. But where's a comparative test of computers using this or similar drives?
 
  [http://www.newegg.com/Product/Product.aspx?Item=N82E16820227499](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227499)
 
 Here-
 
 [http://hothardware.com/Articles/OCZ-ZDrive-m84-PCIExpress-SSD-Review/?page=1](http://hothardware.com/Articles/OCZ-ZDrive-m84-PCIExpress-SSD-Review/?page=1)
 
> **Ulysses_ said:**
> So it does not matter much what computer you put this on as long as the motherboard has a PCI-E x8 socket? Maybe then I ought to go back to magazines for the computer for overall performance/price ratio, and simply add that SSD drive? 800 Mbytes/s is close enough.

800MB/sec is more than you asked for originally.....but its not going to do 800MB/sec. 

> **dragos2 said:**
> I am not an expert but a PCI-E x8 would do a maximum of 2 GB/s theoretically.
[http://en.wikipedia.org/wiki/List_of_device_bandwidths](http://en.wikipedia.org/wiki/List_of_device_bandwidths)

2GB/sec, if you are talking PCIe 1.0 8x. PCIe 2.0 8x has double the bandwidth, up to 4GB/sec.

---

### Post by Ulysses_ on 2010-06-03
> 800MB/sec is more than you asked for originally  Read the OP again, it says *duplicate* a 5 gigabyte file, not just read a 5 gigabyte file (I duplicate files too often as a vmware user).  As calculated above, to read and write that 5 gigabyte file in 10 seconds, the bandwidth is 1 gigabyte/s.  > .....but its not going to do 800MB/sec  Thank you, therefore you agree that we should not compare theoretical speeds of components but compare entire computers benchmarks.  Hence the title.

---

### Post by cascade9 on 2010-06-03
> **Ulysses_ said:**
> Read the OP again, it says *duplicate* a 5 gigabyte file, not just read a 5 gigabyte file (I duplicate files too often as a vmware user).  As calculated above, to read and write that 5 gigabyte file in 10 seconds, the bandwidth is 1 gigabyte/s. 

I'd seen your post where you mentioned 1GB/sec (not the OP BTW). I cant speak for SSDs, but I do know that with mechanial HHDs, coping speds are impacted by how close or far the copy is. E.g.- a 1TB disc, 4 250GB partitions, partitions numbered in order- to copy a file from partition 1 to parttion 2 is faster than to copy to partiton 4. (because to the extra distance that the heads have to move). I only know of one place tht even bothers with 'copy near' and 'copy far' test though, see this link- 

[http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_17.html](http://www.xbitlabs.com/articles/storage/display/1tb-14hdd-roundup_17.html)

I was assuming that you would want to copy from 1 drive to another, not within one drive. ;)

BTW, xbitlabs is very good IMO. Its a good place to look for benchmarking on high-end parts. 

Edit- neat test on (huge, 8 drive) RAID arrays here, some of which might actually do what you want- 

[http://www.xbitlabs.com/articles/storage/display/6-sas-raid-controllers-roundup.html](http://www.xbitlabs.com/articles/storage/display/6-sas-raid-controllers-roundup.html)

> **Ulysses_ said:**
> 
Thank you, therefore you agree that we should not compare theoretical speeds of components but compare entire computers benchmarks.  Hence the title.

Totally agree. Theoretical speeds are just that- theoretical. 

I've had many a discussion about how SATA wasnt one bit faster than PATA on release, even though it had more bandwidth.

---

