---
title: "IBM Thinkpad i-Series 2666 (Partition Problem)"
date: 2012-01-26
forum: Server Platforms
---

### Post by jimmylamhk on 2012-01-26
I have an old IBM Thinkpad i-Series 2666.(192mb ram, Pentium III 750Mhz). I installed ubuntu server 11.10 server on this computer. The harddisk is a Fuijitsu 80G. I partitioned the harddisk into 1.Winxp (66G),2.Linux Root (Ext4,4.7G),3.Linux /home (ext4, about 11G). The computer was frozen when I try to write more than 4.7G(approx.) into the third partition(/home). The computer could only be turned off by pressing the power button for 4 secs. In a nutshell, any  attempt to write more than that size in any partition created by ubuntu will result in DMA read errors which will halt my system. I am quite sure it is not due to hardware problem. Can anyone know how to fix it?

---

