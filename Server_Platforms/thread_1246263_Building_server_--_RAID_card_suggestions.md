---
title: "Building server -- RAID card suggestions?"
date: 2009-08-21
forum: Server Platforms
---

### Post by thk on 2009-08-21
I'm building a server with rough specs
SuperMicro SuperServer 6026T-URF
2xIntel 5560 CPU's
24GB DDR3-1333 RAM
8x1TB SAS disks

I'm adding hardware RAID 6 w/ battery.

I've looked at Intel® RAID Controller SRCSATAWB and SuperMicro AOC-USAS-S8iR controllers.

Use is heavy duty simulation, GIS and manipulating very large datasets (some in PostgreSQL).

I'm not sure how much the RAID card matters. What are your favorites and why? What works well with Ubu? Any benchmarks out there?

---

### Post by windependence on 2009-08-22
With Linux in general, 3Ware cards work extremely well.

I have had good luck with Adaptec 2420 and 2820 cards as well but some OSS purists would like to pi$$ on that idea because Adaptec doesn't share code, but they still work well.

-Tim

---

