---
title: "Most stable nVIDIA low-profile dual-display VDA as of 14.04b3?"
date: 2014-04-07
forum: Ubuntu Development Version
---

### Post by bcschmerker on 2014-04-07
I have been running ongoing tests with Ubuntu® 13.12a1, 14.01a2, 14.02b1, and 14.03b2 on a soup-up of an eMachines®/Acer® EL1210-09 (Advanced Micro Devices® Athlon 64® LE-1620, nVIDIA® MCP78S chipset with integrated 64-bit GeForce® GPU) augmented with a Shuttle® PC6300001 PSU.  As of 7 April 2014, I've had nothing but trouble double-heading this system, using each of two different nVIDIA® GT218-based half-height cards (viz., an EVGA® GeForce® 8400 GS&#8482;, and an Asus® EN210/DI/512MD2(LP) ) for primary and the planar GeForce® for secondary - the planar rarely activated:  Furthermore, I've run into KSOD's on each non-Updates nVIDIA® driver in the Restricted repository for Trusty, and even on occasion with X.org Nouveau - specifically, both monitors up, but neither showing a log-in screen.

I have concluded that the system I am preparing for projection-computer duty will best run on a single GPU.  Due to the need to keep one of the EL1210's two PCIe slots free for a video input board, I am favoring Quadro&#8482; over GeForce® for operational status; the requirement specifically calls for a split harness for dual DVI-I's, as I anticipate future upgrades of both working monitor and projector to digital standards from the initial dual-analog deployment (tests with the EVGA® board cited resulted in DVI-A primary and VGA DE-15 secondary connections needed, the DE-15 being moved to the adjacent slot for access).  From the findings at Phoronix® on the performance handling by GPU for X.org Nouveau, the ideal card is a half-height split-harness model based on the nVIDIA® GT216 GPU, the sole Tesla GPU to have all clocking issues RESOLVED FIXED in X.org; but the GT218, which I have used for tests to date, is acceptable.

Which GT216- or GT218-based half-heights by vendor would be good for this system?  Links to data pages would be appreciated.

---

### Post by bcschmerker on 2014-04-16
Thread closed by Starter, as Ubuntu® 14.04.0-LTS was released with no other Replies received.  According to Phoronix®, X.org Nouveau is dependent on an upgraded Kernel (probable metapackage: **linux-image-generic-lts-utopic**) for full reclocking support on all nVIDIA® GT, GF, and GK graphics-processing units. :-(

---

