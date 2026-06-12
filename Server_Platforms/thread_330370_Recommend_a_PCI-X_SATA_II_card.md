---
title: "Recommend a PCI-X SATA II card?"
date: 2007-01-03
forum: Server Platforms
---

### Post by mcmanus on 2007-01-03
Next order of business:  setup a software RAID5/6 array.

Can anyone recommend a good PCI-X SATA II card?  I'm leaning towards either the

Adaptec 2169300-R (I think is 2420SA)
-or-
3ware 9550SX-4LP

Anybody have any comments on either?  Features, functionality, reliability, speed, driver support, 4 ports or 8 ports, RAID5 vs. RAID6, NCQ, etc.

Also, my server motherboard (Tyan Tiger MPX) only supports 64-bit/66MHz PCI-X, and both cards are rated for 133 MHz.  PCI-X is supposed to dynamically scale from 133->66->33 depending on support.  Will I have any problems with those cards?

Thanks!

---

### Post by mcmanus on 2007-01-03
Actually, I changed my mind...  I'm pretty sure I'm going to go with the Adaptec 2820SA instead and go with RAID6.  Is it possible to setup a RAID6 array with 6 disks (with only one as parity), but add a 2nd (or even 3rd) parity disk later?

---

