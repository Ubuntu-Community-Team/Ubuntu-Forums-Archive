---
title: "Recomended Hardware"
date: 2010-04-28
forum: Server Platforms
---

### Post by CatWeazel67 on 2010-04-28
Hi,

I have been using Linux for several years to run services for a small primary school (under 12&#8217;s). We are about to buy a new server and I would appreciate advice on a hardware specification.

There will be approximately 450 users with probably between 30 and 60 users connecting at any 1 time.

The server will be running Samba,CUPS,LDAP.

I know we can never have enough disk space :) My main question is how much RAM should I be looking at and any recommendations for processor ? Or generally other advice on choosing hardware. Budget around 1,000 GBP ( ex VAT / tax etc)

Thanks for you time

---

### Post by Vegan on 2010-04-28
A file server is happy with 4 GB of RAM to hold the indices. This assumes the 64-version of Linux.

Using a real RAID card is the best way to provide a safe and stable storage solution. Then this array is independent of the boot disk and if you need to repair that, the array is safe.

I am looking at the HighPoint 2640X1 which is a low-end PCIe SAS controller for managing backup equipment.

A more complex controller is useful for larger arrays.

HighPoint has gone open wiht their drivers so Linux likes them a lot.

I have used HighPoint before and they are good.

---

### Post by BobVila on 2010-04-28
None of that stuff should be super-intensive. I'd agree with the 4GB of RAM. As far as processors go, anything even relatively modern should be fine. A HW RAID card will take a bit of the stress off of the proc, too, although that's less relevant now than it once was. You major bottleneck will likely be network throughput. If it were me, i'd probably scale back on processor speed and get a secondary NIC to help spread the load. (That assumes you can set up lacp on the switch side)

---

