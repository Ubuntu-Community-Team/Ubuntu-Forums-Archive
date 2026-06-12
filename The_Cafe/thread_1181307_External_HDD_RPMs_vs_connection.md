---
title: "External HDD: RPMs vs connection"
date: 2009-06-07
forum: The Cafe
---

### Post by Vostrocity on 2009-06-07
Does anyone know which one is the bottleneck for external HDDs? For example, if I have a 5400RPM drive does it mean eSATA (or Firewire) is unnecessary? What about 7200RPM?

---

### Post by Skripka on 2009-06-07
> **Vostrocity said:**
> Does anyone know which one is the bottleneck for external HDDs? For example, if I have a 5400RPM drive does it mean eSATA (or Firewire) is unnecessary? What about 7200RPM?

If you're using USB2 or firewire-the bus will bottleneck before the drive itself will.

If you're using eSATA, the drive speed will be the bottle neck.

(Presuming a modern current generation HDD)

RPM is not the be all end all determiner of speed.  It also depends on what you are doing, as well as the drive size (density), and drive cache.

---

### Post by Therion on 2009-06-07
Edited.

---

### Post by Vostrocity on 2009-06-08
> **Skripka said:**
> If you're using USB2 or firewire-the bus will bottleneck before the drive itself will.

If you're using eSATA, the drive speed will be the bottle neck.

(Presuming a modern current generation HDD)

RPM is not the be all end all determiner of speed.  It also depends on what you are doing, as well as the drive size (density), and drive cache.

So if I get this right, the order from slowest to fastest is this.
-USB 2.0
-Firewire
--5400RPM
--7200RPM
-eSATA
I know it's not very accurate to compare RPM to Mbps but I just getting a rough estimate.

---

### Post by Firestem4 on 2009-06-08
> **Vostrocity said:**
> So if I get this right, the order from slowest to fastest is this.
-USB 2.0
-Firewire
--5400RPM
--7200RPM
-eSATA
I know it's not very accurate to compare RPM to Mbps but I just getting a rough estimate.

Not totally true.

eSata and a 7200RPM SATA Hard Drive operate at the same speeds which is 3.0GiB/s. (A 5400 RPM HDD is 2.0GiB/s).

You will notice no difference between the two as they are essentially the same device (Just one is pointed towards the outside of the computer).

The only drawback (I believe, however it is being addressed) is that eSata does not provide a self-powered feature like USB does (depending on device).

---

### Post by Skripka on 2009-06-08
> **Firestem4 said:**
> Not totally true.

eSata and a 7200RPM SATA Hard Drive operate at the same speeds which is 3.0GiB/s. (A 5400 RPM HDD is 2.0GiB/s).

You will notice no difference between the two as they are essentially the same device (Just one is pointed towards the outside of the computer).

The only drawback (I believe, however it is being addressed) is that eSata does not provide a self-powered feature like USB does (depending on device).

Even if they do address bus powering on eSata-USB3 comes out in less than a year with 5GiB/sec bandwidth...there isn't that much point.

---

### Post by Vostrocity on 2009-06-09
Actually I was thinking of a 5400RPM drive and a 7200RPM one housed inside a case with USB, Firewire, or eSATA. So based Skripka's first post, I'm concluding that USB and Firewire bottlenecks the drive, but eSATA does not.

---

### Post by Firestem4 on 2009-06-09
If it gives you anything to consider. I am running my main linux distro off of an external USB Hard Drive. its a 5400RPM 2.5" notebook drive connected via USB2.0.

It runs very good...Admittedly file transfers are slow. But for 480mb/s compared to a normal computer operating speed of 2-3.0gb/s, it runs remarkebly well. (In fact my Arch install runs faster than Vista, vista is on the laptop HDD's connected with SATA). Go figure!

---

### Post by ssam on 2009-06-09
there are 2 speed figures that matter for disks. throughput and latency. when you read a file you have to wait for the read head to move to the right bit of the disk, and for the disk to rotate to where the file is stored. once there you read at the throughput speed until you need to jump somewhere else. high RPM helps with both, but there are other factors.

the through put of the drive is usually lower than the interface. (no drive gives 3Gb/s). also firewire and USB are generic interfaces so not as optimised for disks as SATA/eSATA. It is often noted that firewire 400Mb/s gives faster fire transfers than USB2 at 480Mb/s. 

i recommend you have a look through this article that compares some disks using USB, FW and eSATA 

[http://www.tomshardware.co.uk/-external-hard-drive,review-31383.html](http://www.tomshardware.co.uk/-external-hard-drive,review-31383.html)

---

### Post by Vostrocity on 2009-06-09
Thanks for the info. I've decided that I'll have to stick to a USB case for my 2.5" 5400RPM drive for the sake of compatibility. Only two computers in my house have Firewire, and none have eSATA.

---

### Post by gn2 on 2009-06-09
Reliability and ease of use are more important than speed.

Higher RPM does not always guarantee higher transfer speed, there are a number of other things to consider.

[http://www.tomshardware.com/charts/2.5-hard-drive-charts/Maximum-Write-Transfer-Performance,686.html](http://www.tomshardware.com/charts/2.5-hard-drive-charts/Maximum-Write-Transfer-Performance,686.html)

---

### Post by mips on 2009-06-09
> **Skripka said:**
> Even if they do address bus powering on eSata-USB3 comes out in less than a year with 5GiB/sec bandwidth...there isn't that much point.

USB theoretical & actual troughput are two completely different things. I will wait and see what actual throughput USB3 delivers before jumping to any conclusions.

---

### Post by kc3 on 2009-06-09
The RPMs and connection or two totally different factors but equally important. Think about it this way, in computers the information transfers through many different places but during the transfer it's only as fast as the slowest part. It's like, if you have a 500KB/s internet connection and a 50MB/s network connection, upgrading to a 100MB/s connection is not going to increase your internet at all. Really Sata and Sata II even really make little difference other than on high end Solid State Drives and forms of them like a GC-RAMDISK because the hard drive speed is the slowest part. A 10,000RPM hard drive will act much faster than a 5,400RPM hard drive regardless of the connection. USB 1 though is not that fast and could be a bottleneck however USB 2 should still be pretty good.

SataII can transfer up to 3GB/s, and SataI I believe is 1.5GB/s, but you won't find a hard drive that actualy runs anywhere near 1.5GB/s, at the MOST maybe 200MB/s unless you have a bunch of hard drives RAIDed together or have a really really high end drive. The GC-RAMDISK I think can run at like 600MB/s

My 10,000RPM hard drive is only a SataI connection but the 7,200RPM one is on a SataII, which would you think is faster? Well, the max speed isn't MUCH better on the 10,000RPM one but the average and the slowest it gets are way higher than on the 7,200RPM one.

---

### Post by Skripka on 2009-06-09
> **kc3 said:**
> 
SataII can transfer up to 3GB/s, and SataI I believe is 1.5GB/s, but you won't find a hard drive that actualy runs anywhere near 1.5GB/s, at the MOST maybe 200MB/s
.

Ummm...You realize that the SATA standard is defined in terms of Gigabits/second not Gigabytes/second, don't you?

You realize that 1.5Gbit/sec is about 200Megabyte/sec--do you not?  SATA 1.5 should NOT run at 200Megabyte/sec or higher ipso facto.  You factor in the 80% rule of bits-and you end up with the real world 150MB/s.

Don't mix units-and the world is much less confusing.

SATAII was drafted at 3.0Gbit/s (real world 300MB/s) to allow lots of room for the future.

---

### Post by kc3 on 2009-06-09
lol, well, I've been mixing them up, still it holds, 200 is still really for high end drives, majority of hard drives still don't get nearly that high, at least not by themselves. Plus also, I did the benchmarks and my Sata I 10,000RPM hard drive still out performs my 7,200RPM Sata II hard drive.

Like I said though, max speed are very similar but the 10,000RPM one seems to keep a higher average (though I do agree it's more likely to go bad)

Sooo in conclusion unless you're comparing IDE and Sata I really wouldn't worry about the connection a whole lot unless you're using really high end drives.

---

