---
title: "LTSP Ubuntu 11.04 and Precision workstations"
date: 2011-11-14
forum: Server Platforms
---

### Post by phanh on 2011-11-14
Hello, all

After few days spent setup LTSP on Ubuntu 11.04, we have a computer lab again! 

We, however, have an issue. The lab is made of Optiplex GX280 Pentium 4, Precision 360 P4, and Precision 590 Xeon. 
The optiplex boot successfully. 
The Precision 360 stop at "Loading xxx.xxx.xxx.xxx/ltsp/i386/nbi.img (ELF)...Done
The Precision 590 stop at "Loading xxx.xxx.xxx.xxx/ltsp/i386/nbi.img (ELF)...Done" Issuing RESET

The main difference is during boot time, we saw the Optiplex use PXE to boot while the Precision use Etherboot.

So we follow this [tutorial]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPEtherbootSetup") to setup LTSP boot using Etherboot. It seems like an old tutorial because when running mknbi-linux, we received warning "mkelf-linux is preferred in future instead of mknbi-linux"

Anyone have info on setup ltsp etherboot on Ubuntu 11.04? Will etherboot nbi allows the optiplex clients to boot using pxe?

Any advice or info is greatly appreciate.

---

