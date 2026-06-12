---
title: "mdadm &amp; volume manager ate all my performance!  Why?"
date: 2010-07-07
forum: Server Platforms
---

### Post by pootle42 on 2010-07-07
I've been trying to track down why a hosted ubuntu (hosted with KVM) is suffering from rather poor performance, and the issue seems to be around mdmad.  I've done some basic checking with hdparm to try and see what is going on and mdadm + volume manager seem to be giving me a big performance loss.

Am I doing something silly here or is this just the way it is?  Maybe I should try the motherboard raid controller (although I'm not to keen on that idea).  I do have an old 3Ware 9650 card, but it threw a wobbly every time the machine was powered off and on, and when I went on holiday all hell broke loose (the battery had gone flat, but as the machine had been cleanly closed down, I didn't see why that should be a problem – but that's another story...)

I have a raid 10 array of 4 2.5” 7,200 rpm laptop discs (as a compromise between speed, power and noise).

The resultant volume I access through volume manager on top of mdadm has about ½ the read performance (as reported by hdparm) of 1 of the underlying physical discs.  I was expecting double (or a bit better).  What is going on?

Here is the typical output of hdparm on one of the underlying discs:
```
/dev/sdc:
 Timing cached reads:   1922 MB in  2.00 seconds = 961.12 MB/sec
 Timing buffered disk reads:  178 MB in  3.02 seconds =  58.88 MB/sec

```

This figure is pretty consistent on all 4 discs and repeatable +/- 6MB/sec

Now if I look at the mdadm device:
```
/dev/md0:
 Timing cached reads:   1934 MB in  2.00 seconds = 967.04 MB/sec
 Timing buffered disk reads:  166 MB in  3.02 seconds =  54.96 MB/sec
```


And the resultant volumes:
```
/dev/gendata/vmdata:
 Timing cached reads:   1930 MB in  2.00 seconds = 964.88 MB/sec
 Timing buffered disk reads:  118 MB in  3.01 seconds =  39.17 MB/sec
```

The machine is running:

2.6.31-20-server #58-Ubuntu SMP Fri Mar 12 05:40:05 UTC 2010 x86_64 GNU/Linux

Where's all my performance gone?  Given this is a sequential read test, I wouldn't expect any issues with physical / logical alignment to be causing a problem.

I would expect a RAID10 set in sequential read mode to be giving at least 2.5 &#8594; 3 times the performance of a single disc....

---

### Post by fjgaude on 2010-07-08
I can't say for sure what's going on, but raid 10 is less than twice the thru-put of one drive alone. The rest may be your slow memory and CPU, can't really say.

Here's mine with four raid5 Samsungs (old), CPU at 3.6GHz:

```
/dev/md32:
 Timing cached reads:   18182 MB in  2.00 seconds = 9103.61 MB/sec
 Timing buffered disk reads:  540 MB in  3.00 seconds = 179.75 MB/sec

```

Notice my signature.

---

