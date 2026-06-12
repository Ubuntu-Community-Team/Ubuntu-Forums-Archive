---
title: "Software RAID0 For Solid State Storage Devices"
date: 2009-03-06
forum: Ubuntu Brainstorm
---

### Post by Maduroutmb on 2009-03-06
I am interested in the potential that solid state storage has for minimizing or eliminating the storage bottleneck.  Specifically, I want to address the lack of direction that current SSD technology displays.  It seems that flash storage drives are trapped in the paradigm from HDDs, in which a storage drive must be an autonomous device connected via a low-bandwidth, high-latency, long-cord connection (SATA).  Further, for HDDs, a RAID0 is a performance enhancing organizational system that highlights a disk drives' propensity to fail.  

In contrast, a SSD has very good reliability (very predictable failure modes) and depends upon RAID0 for performance (which it can do because increasing the number of RAID devices to a number that would be insane with HDDs carries little risk with flash blocks).  A modern SSD is essentially an x86 ARM chip with SDRAM controlling blocks of flash memory and connected to the computer via an SATA connection.  This diagram is likely familiar to most of you, but it sparked my interest in this topic:

[IMG]http://www.hothardware.com/articleimages/Item1211/ssd-block-diagram.png[/IMG]

  My question is with regard to using a software RAID0 to directly control the blocks of flash memory over a high bandwidth bus (HT, QPI, PCIe, et c.). Obviously, the software driver would need to control wear leveling and store at least some address data on the SSD itself (but not in the RAID0 array blocks).  I know that I'm not competent to ask all of the relevant questions, but that's the purpose of the thread.  

Finally, I asked a similar question on AMDzone, and was alerted to the existence of Fusion IO, a company that makes PCIe storage cards ([http://www.fusionio.com/Products.aspx]("http://www.fusionio.com/Products.aspx")). While that product uses a high bandwidth bus, it still uses an internal controller and costs $3-14k USD.

---

