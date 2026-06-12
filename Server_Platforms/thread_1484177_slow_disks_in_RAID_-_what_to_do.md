---
title: "slow disks in RAID - what to do?"
date: 2010-05-15
forum: Server Platforms
---

### Post by davidmaxwaterman on 2010-05-15
Hi,

My system has an 6(+2 spare) disk md RAID5 (in addition to other disks) and I was just idly playing with the Disk Utility and used it's 'Benchmark', the Read-Only one, to test each of the disks, and the whole array.

As a whole, I get :

Minimum Read Rate: 88.1 MB/s
Maximum Read Rate: 144.8 MB/s
Average Read Rate: 122.0 MB/s
Average Access Time: 16.5 ms

and most of the disks in the RAID seem to get something like this :

Minimum Read Rate: 35.6 MB/s
Maximum Read Rate: 62.3 MB/s
Average Read Rate: 53.4 MB/s
Average Access Time: 13.4 ms

However, there are couple which get more like this :

Minimum Read Rate: 18.3 MB/s
Maximum Read Rate: 28.1 MB/s
Average Read Rate: 24.4 MB/s
Average Access Time: 14.2 ms

This looks something like 1/2 of the faster ones.

The drives are all "the same" :

Device Model:     WDC WD2000JB-00EVA0 *
Device Model:     WDC WD2000JB-00EVA0 *
Device Model:     WDC WD2000JB-00GVA0
Device Model:     WDC WD2000JB-00KFA0
Device Model:     WDC WD2000JD-19HBB0
Device Model:     WDC WD2000JD-19HBB0
Device Model:     WDC WD2000JD-00HBB0
Device Model:     WDC WD2000JD-00HBB0

I've marked the slow drives with a '*'.

Note that the first four are PATA connected to a four port HPT374 PCI card, and the latter four are SATA connected via the mobo's MCP55 SATA Controller.

Both the slow drives are part of the array proper (ie not slaves). The other two PATA drives are the slaves.

I wonder :

1) is there anything to worry about with the two slow drives?
2) is there anything I can do to bring their performance up to that of the others (firmware upgrade or something)?
3) would there be a performance increase if I switched the slow and fast PATA drives?
4) would the performance increase be noticeable and worth the effort?

Any other advice?

Max.
PS. I'm using 10.4/2.6.32-22-generic-pae - not the server distro.

---

### Post by Th3_uN1Qu3 on 2010-05-15
Try playing around with the hdparm command, more specifically check that the DMA flag is set properly. I used to do that all the time. Nowadays it should be mostly automatic but it never hurts to try... Just make sure you set the exact same parms to both drives since they are in RAID, and don't set DMA to silly values or you may corrupt the data.

---

### Post by davidmaxwaterman on 2010-05-16
> **Th3_uN1Qu3 said:**
> Try playing around with the hdparm command, more specifically check that the DMA flag is set properly. I used to do that all the time. Nowadays it should be mostly automatic but it never hurts to try... Just make sure you set the exact same parms to both drives since they are in RAID, and don't set DMA to silly values or you may corrupt the data.

I just get error messages from that command :

"$ sudo hdparm -d /dev/sdc
/dev/sdd:
 HDIO_GET_DMA failed: Inappropriate ioctl for device
"

I guess this command doesn't work for this kind of drive?

Max.

---

### Post by dtfinch on 2010-05-16
24.4mb/s (slow drive) * 5 (6 minus parity) = 122mb/s (your total speed), so those two probably are slowing the rest down.

Your next bottleneck after fixing that might be the PCI card, which maxes out at 133mb/s, but it might not be a problem since it only has two drives in use.

The main issue on my first/last raid 5 (3ware) was poor write performance. But I had left the raid card's write cache disabled because I didn't have a battery backup. I haven't tried raid 5 with mdraid.

---

### Post by davidmaxwaterman on 2010-05-16
> **dtfinch said:**
> 24.4mb/s (slow drive) * 5 (6 minus parity) = 122mb/s (your total speed), so those two probably are slowing the rest down.

Your next bottleneck after fixing that might be the PCI card, which maxes out at 133mb/s, but it might not be a problem since it only has two drives in use.

I wonder how best to convert the raid into using the faster two PATA drives in place of the slower two?

I will try failing them one at a time and letting the array rebuild using the spares.

Max.

---

### Post by davidmaxwaterman on 2010-05-16
> **davidmaxwaterman said:**
> I wonder how best to convert the raid into using the faster two PATA drives in place of the slower two?

I will try failing them one at a time and letting the array rebuild using the spares.

Max.

Now my array is :

Minimum: 142.4 MB/s
Maximum: 286.8 MB/s
Average: 203.6 MB/s
Access: 16.3 ms

That's up from :

Minimum Read Rate: 88.1 MB/s
Maximum Read Rate: 144.8 MB/s
Average Read Rate: 122.0 MB/s
Average Access Time: 16.5 ms

I'm quite pleased with that improvement :)

I wonder what to do about the slow disks. It seems to me like it is a firmware issue :/

Max.

---

