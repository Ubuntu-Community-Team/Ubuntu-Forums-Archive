---
title: "Ubuntu Server 14.04 boot issue with Dell Poweredge 2950"
date: 2015-05-14
forum: Server Platforms
---

### Post by Dangerousdave26 on 2015-05-14
I recently bought a Dell Poweredge 2950 with a perc /6i RAID controller. It has 6 x 300GB in RAID 6.

I must have loaded Ubuntu server 14.04 today a dozen times. Each time it would get the point it should start to boot and it just hung there doing nothing but blinking cursor. 

Long story short to fix it I had to boot to Parted Magic and run Boot Loader Restore Utility. 

Now it boots fine. 

I just wanted to post my findings in the event anyone else has the issue.

---

### Post by LHammonds on 2015-05-16
That's odd.  I have a couple of Dell PowerEdge 2850 servers with same RAID setup (total 366GB space available).  Have not had that issue.

I'll be sure to keep this in mind if I do though.  Thanks for the info.

LHammonds

---

