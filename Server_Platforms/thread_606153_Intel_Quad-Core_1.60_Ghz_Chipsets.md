---
title: "Intel Quad-Core 1.60 Ghz Chipsets"
date: 2007-11-07
forum: Server Platforms
---

### Post by JCorrea920 on 2007-11-07
On install does Ubuntu have drivers for Intel Quad-Core 1.60 Ghz Chips? Could I use Dapper LTS? What if the server has two chips?

---

### Post by agent8131 on 2007-11-08
No drivers are needed for the cpu. They will work fine, with 1, 2, or more.

Now if you mean for a particular chipset (northbridge/southbridge) and/or motherboard that might be a different story.

---

### Post by JCorrea920 on 2007-11-09
I am not sure what you mean by northridge/southridge ?  All I know is that it is Intel Chipset on a Dell PowerEdge 2900. Can I use Dapper or do I need 7.10?

---

### Post by Bachstelze on 2007-11-09
This would be the first time I hear about a multi-core NB/SB... You are most certainly talking about the processor (CPU), which will indeed work just fine in Dapper, provided you install a SMP kernel.

---

### Post by JCorrea920 on 2007-11-10
Can I install smp kernel option during Ubuntu Installation? How do I set this option? I also noticed in the bios that the CPUs are 64-bit so I had to download the Dapper Server iso for 64-bit. Am I on the right track?

---

### Post by agent8131 on 2007-11-11
The default kernel is smp aware.  I would recommend going with the 64-bit ISO but it is worth mentioning that the 64-bit version will not easily run 32-bit software without some additional effort.  The chipset on the PowerEdge 2900 appears to be the Intel 5000X.  This should work with the Dapper kernel though a more recent kernel might offer more features and/or performance.

---

