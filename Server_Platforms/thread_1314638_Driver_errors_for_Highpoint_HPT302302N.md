---
title: "Driver errors for Highpoint HPT302/302N"
date: 2009-11-04
forum: Server Platforms
---

### Post by renetwist on 2009-11-04
Hello,

Before I continue, I believe that a quick system overview might be good for a more specific answer.

System specification:
[LIST]
[*]**Motherboard**
*Asus A8V-VM SE*
[*]**CPU**
*AMD Athlon 64 4000+*
[*]**Memory**
*2GB DDR*
[*]**Additional PCI cards**
*Highpoint HPT302/302N*
[*]**HDD0**
*Maxtor PATA 200GB [onboard controller 0]*
[*]**HDD1**
*Samsung PATA 200GB [HPT controller 0]*
[*]**HDD2**
*Samsung PATA 200GB [HPT controller 0]*
[*]**HDD3**
*Samsung PATA 200GB [HPT controller 1]*
[*]**HDD4**
*Samsung PATA 200GB [HPT controller 1]*
[*]**DVD0**
*TSSCORP DVD-ROM [onboard controller 1]*
[/LIST]

I wanted to install the latest server edition of Ubuntu. The installation worked like a charm and I didn't even need to apply [this]("http://ubuntuforums.org/showthread.php?t=953568") solution. But when I was trying to partition the drives located on the HPT controller I got allot of I/O errors. Those I/O errors were only seen on HPT controller 1. What I have done so far is this:

[LIST]
[*]Used different PATA cables
[*]Used different PCI slot for the HPT controller
[*]Did full testing of drives using ESTOOL from Samsung [no errors]
[*]Eventually did a Low Level Format on each Samsung drive
[/LIST]

All this did not solve the I/O errors. For now I reinstalled 8.04 LTS server and used [this]("http://ubuntuforums.org/showthread.php?t=953568") solution.

And hey! I could partition the drives perfectly. No errors whatsoever. Could it be that the 9.10 drivers for the HPT controller are broken in some way?

I hope you guys could shine a light on this issue.

Sincerely yours,

René Jansen
The Netherlands

---

