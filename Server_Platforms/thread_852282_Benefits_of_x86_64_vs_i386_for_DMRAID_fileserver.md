---
title: "Benefits of x86_64 vs i386 for DMRAID fileserver?"
date: 2008-07-07
forum: Server Platforms
---

### Post by sp00ki on 2008-07-07
I'm preparing to configure a fakeraid system as a dedicated file storage box.
I've been doing a bit of investigating and am not quite convinced as to whether or not i'd benefit from running x86_64 over i386 ubuntu (8.04).
I'll be using SAMBA; the system will have the following specs:

-Celeron D 352 (3.33GHz) CPU
-2GB DDR2 (pc2 5300) RAM
-4x 400GB 7200RPM SATA drives (raid5, DMRAID)
-ECS NFORCE 570 SLIT-A LGA775 mobo

The system will see moderate I/O, not "enterprise" load by any means; average traffic will typically consist of a user streaming music while editing large image files, another streaming video, and maybe one or two bittorrent sessions (the above examples will all be written to/read from the fileserver by other hosts on the network).
The system will see more than the above on occasion, but not regularly.
The network is a gb one, so i don't foresee bottleneck there.

I've seen benchmarks illustrating x86_64 systems excelling over their i386 counterparts when handling jobs like file encoding, etc., but actually performing (slightly) worse in other instances.
Does anyone know how the two platforms compare when driving software raid?

Additionally, are there any drawbacks to using dmraid over mdadm?  I'm a bit of a n00b to software raid solutions...

**ED:  the OS will be on a fifth ultra ata 133 drive, not the array*

---

### Post by fjgaude on 2008-07-07
I can't say you will notice any difference in through-put, 32- versu 64-bit. I still would go with the 64-bit.

As to **dmraid** versus **mdadm**... no contest. dmraid I don't think handles raid5, at least it didn't a year or so ago, and lacks flexibility. I use mdadm, but it has been a big learning curve to understand how to handle it over the years, drive failures, spares, etc. The creation was easy... it's been when things needed to be changed... using the **man mdadm** pages has been a pain. You might like to read, study all of this link:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)

Let us know how you are doing.

---

### Post by sp00ki on 2008-07-07
definitely will, thanks!
this is a good start, though i'm curious-- why would you choose 64bit if not for difference in throughput of this specific application?  I'm going to try to research this a bit, but i'd hate to waste a week building raid arrays and benchmarking if someone's already done this sort of work...

---

### Post by sp00ki on 2008-07-07
i also have another question which i'm hoping to further clarify.
the four raid disks will be sata 2 disks; however, the OS disk will be ata 133.  since the raid array will be a separate partition altogether, my initial thought is that the ata 133 disk won't come into play as a potential bottleneck (at that point, all the talking is done between cpu/ram/raid disks).  is this completely accurate?  will the ata 133 drive ever be a consideration (potential hindering performance), or was my initial thinking correct?

---

### Post by fjgaude on 2008-07-07
Well, from what I understand, to have two different controllers, one for the raid and another for the OS is a big advantage. So that's that.

Well, 32/64 is really about whether you will ever use more than that 2G of RAM... the 64 hanldes it better as you get to 4 and beyond. 32 goes only to 4 and usually doesn't, isn't able to use it all, leaving up to 600M behind. 64 usually handles it all very nicely. In the issue of programs and drivers and the like, 64 is here now... 32 is slowly falling in the background, because all the CPUs are 64-bit.

Anything else?

---

### Post by sp00ki on 2008-07-07
there's far more to x86_64 vs i386 than just memory utilization. for instance, this article compares the two (both using 2GB RAM):
[http://www.phoronix.com/scan.php?page=article&item=616&num=1](http://www.phoronix.com/scan.php?page=article&item=616&num=1)
as you can see, there's a difference in the performance of either platform depending on the application, memory not being a factor in this case.
what i'm looking for is someone with knowledge of the platform differences to perhaps provide insight into which "handles" software raid more optimally.
I'll be using 2GB in the system, so approaching or surpassing 4GB isn't an issue.

---

### Post by fjgaude on 2008-07-07
I've read the article... not much difference and what there is I wouldn't believe it is repeatable. The kernels are constantly changing, hopefully for the better. And the apps are taking advantage of the 64-bit registers now.

I have a dual-boot situation on my main box, one is 32, the other, 64. I can tell no difference between the two. The same four-disk raid5 array is used by each as it handles my main database. I've had such for a long, long time, four years, just watching what the differences are between the two versions of Ubuntu are... nowadays, they are about the same. I run 4GB of RAM... in 64-bit 3.9GB shows; in 32, 3.5. Go figure.

I'm a graphic designer and use much CPU to do what I do and either shows the same work through-put.

---

### Post by sp00ki on 2008-07-07
interesting.
i was hoping to find a definite difference between the two, but perhaps there's not.  if i don't find anything, i'll post up some benchmark results, as i'm a bit curious even if the difference is minimal.

thanks for the advice!

---

### Post by windependence on 2008-07-07
Well, the consensus is usually that if you don't need the 64 bit data width, it might actually slow you down. Aside from the memory issue, there aren't too many advantages, and right now in some applications and even some OS's stability is still a problem. 

Personally, I have had the best luck with SuSE and CentOS. My forays into Ubuntu server 64 have unfortunately not been stellar. I have a server class box right now I would love to install it on, but after it's running for a while with no applications loaded, it just pukes - kernel panic, and I can't figure out why. This could well be something I did, but I have had this experience with other 64 bit OS's as well. It's kinda a crap shoot. If you get something that works well and likes your hardware, then go with it. Otherwise, 32 bit may even be faster and more stable.

-Tim

---

### Post by fjgaude on 2008-07-07
Where difference is seen is for aritmatic processes that use integers and the 64-bit wide registers come into play. For raid the XOR function is the issue along with sometimes writing parity bits to all the drives... either 32-bit or 64 is plenty wide enough to do these jobs.

As the apps come up to speed, especially using more than two cores, then 64-bit shows some small advantage. Handling big cache is where 64 shines... as I boot up and start to use all my programs, all of them are in cache, and no disk activity is needed... very quickly I've used all 4GB, and I like it. Next box will likely have 8GB of DDR3 memory.

Let us know of your benchmark testing. I use only **hdparm -tT /dev/md[nn]** for testing. Here's what my humble box produces:

With Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz), CPU fan at 908 RPM; no-load, temp=24C; under max load, temp=41C, fan=1167 RPM; VCore=1.39/1.38v:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   18948 MB in  2.00 seconds = 9487.52 MB/sec
 Timing buffered disk reads:  644 MB in  3.00 seconds = 214.42 MB/sec

```

hdparm is a very versatile program, eh?

---

### Post by sp00ki on 2008-07-07
i definitely will.  depending on how quickly i can get everything up, i may compare filesystems too.  i'm most likely gonig to go with xfs, but i may benchmark it against ext3 just so there's a little more data out there.

---

