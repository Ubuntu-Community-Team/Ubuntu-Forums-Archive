---
title: "Small Business Server starting from Scratch"
date: 2015-07-07
forum: Windows
---

### Post by Roderick_K._Duet on 2015-07-07
Looking for advice / best practice for building and commissioning a small business server.
Goals.
Hardware
No specifics on Processor or Board yet.
Server class processor - Min quad core.
Server class board - defined by processor and RAM selection.
DDR3-1600 Ram 240 pin- as I have 32 gig available.
SATA hard drives - as I have 5 TB available.

Software 
ESXi as Hypervisor base.
Using VM for a Linux based server application.

What I want to accomplish
Would like provisions for at least 6 zero/thin VDI clients running windows 7.
With either a Synced Mobile, VDI or RDP solution for the road.
We are trying to speed up our accounting system which is AccountEdge Pro, it is not really designed for networking to the database as we are doing, and it is very slow. 
My intention is to create the server with the software and database - which is proprietary - on the server where each user would have local access.
The Thin or Zero Client would also be a big improvement to eliminate latency.
I am very new at the server side of things and really need some advice especially on software. I know VMware has solutions for what I am trying to do, 
but from what I am reading their solutions are designed for much larger enterprise and price points are out of my range.
I am in Powder Springs GA. 

Thanks in advance for for any help.
Roderick K. Duet
CEO
Industrial Processing Systems, Inc.

---

### Post by HermanAB on 2015-07-07
Hmm, this is not a Windows support site, but anyhoo, you are a newb with a problem that can be partially handled by Linux:
Windows small business server can do what you want, without the need for VMware.
You just need to buy the necessary remote desktop licenses.

Then you can access the remote sessions either from a desktop Windows machine, or from a Linux machine using 'rdesktop'.

---

### Post by bcschmerker on 2015-07-07
I'm in the process of researching a small-business server project to replace a Gateway®/Acer® DX-series, and I see your memory as an immediate problem:  Server-class means fully buffered and registered 72/144-bit, which I have not encountered to date in DDR3-1600, unlike DDR3-1066 and DDR4-2133.  ASUSTeK Computer, Inc., has several different server 'boards for the Intel® Xeon Processors® with C200- and C600-Series Peripheral Controller Hubs, in addition to Workstation 'boards with the Z97 (FCLGA 1150) and X99 (FCLGA 2025, for '2011v3 MPU's) Express Sets.

My own requirements have me leaning toward an Intel® Xeon Processor® E5-1600v3 Series (FCLGA 2025; clocks TBD as of 7 July 2015), Asus® X99-E WS mobo, an 8 x 4 GiB configuration in Samsung® DDR4-2133 ECC RDIMMs, and an Intel® 950-Series PCIe x4 solid-state drive.  Even with SATA, the hard drives need to be safe to 60°C operating; Western Digital® Caviar Red® is available in five capacities.

---

