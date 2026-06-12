---
title: "PCIe RAID controller with 4 Intel SSDs"
date: 2011-01-12
forum: Server Platforms
---

### Post by joker535 on 2011-01-12
I have been thinking about upgrading my RAID setup from a pair of Intel X25s running the software based RAID included with ubuntu to four Intel X25s running off a PCIe based controller. The controller is an HP P400 which I know works great on ubuntu (I have other machines running it with SAS drives). My desktop has an Intel S5000XVNSATAR mainboard and I have an open PCIe v1.0 8x (physical) slot that is wired 4x. The controller is 8x and will fit fine. 

How much of a performance hit do you think I will see running this 8x controller in the slot wired 4x with four Intel x25s in a RAID 10? Will I have enough bandwidth with the 4x for those SSD's?

Thanks

Bob

---

### Post by rubylaser on 2011-01-12
I don't get very good performance out of either of my p400 controllers in my HP servers even when they're in 8x enabled slots.  Here's hdparm on a RAID 5 array with 8 10,000 RPM SAS disks.

```
root@svr-cc-marketing:~# hdparm -tT /dev/cciss/c0d0

/dev/cciss/c0d0:
 Timing cached reads:   6434 MB in  2.00 seconds = 3218.77 MB/sec
 Timing buffered disk reads:  482 MB in  3.01 seconds = 160.39 MB/sec

```

That's very slow for 8 SAS disks, and my other machine is more around 120MB/sec.

---

### Post by Skadork on 2011-01-12
> **joker535 said:**
> I have been thinking about upgrading my RAID setup from a pair of Intel X25s running the software based RAID included with ubuntu to four Intel X25s running off a PCIe based controller. The controller is an HP P400 which I know works great on ubuntu (I have other machines running it with SAS drives). My desktop has an Intel S5000XVNSATAR mainboard and I have an open PCIe v1.0 8x (physical) slot that is wired 4x. The controller is 8x and will fit fine. 

How much of a performance hit do you think I will see running this 8x controller in the slot wired 4x with four Intel x25s in a RAID 10? Will I have enough bandwidth with the 4x for those SSD's?

Thanks

Bob

pcie 4x bandwidth is something like 2Gbyte/s...I wouldn't think 4 disks would even touch half that bandwidth :/

---

### Post by cascade9 on 2011-01-12
That motherboard only has PCIe 1.x slots, so 4x is only 1000MB/sec. 

[http://ark.intel.com/Product.aspx?id=46538](http://ark.intel.com/Product.aspx?id=46538)

Depending on what model X25s, they can go to 250MB/sec +. So if you've got fast X25s, yeah, 4x PCIe 1.x will be a bottleneck, at least slightly.

---

### Post by joker535 on 2011-01-12
I'm using the X25v 40g ones so they are not the real high performance ones. I thought the 1G of bandwidth would be enough for them but I wasn't sure.

Thanks

Bob

---

