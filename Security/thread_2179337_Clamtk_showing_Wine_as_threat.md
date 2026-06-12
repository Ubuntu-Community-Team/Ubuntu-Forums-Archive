---
title: "Clamtk showing Wine as threat?"
date: 2013-10-07
forum: Security
---

### Post by Barsoom88 on 2013-10-07
I just ran Clamtk and it was showing 39 potenial threats all Wine IDs. 
Any thoughts?

---

### Post by Amorphous Serendipity on 2013-10-08
Hi Barsoom88,

If Clamtk is marking Wine components as a threat  then you should be fine. If it is marking programs that you installed in  Wine as a threat, that is a different story. Remember Wine isn't  actually Windows, so Clam is most likely catching what it believes to be  spoofed of modified Windows components (which depending on how you look  at it, that's fairly accurate). I've had this happen with other AV  programs that can run in Linux, such as COMODO.

If your worried  about it, you can set up a VM with Ubuntu and Wine installed and run the  same scan. If a clean Wine install provides you with the same results  then you know you're okay.

---

### Post by Barsoom88 on 2013-10-09
AhKmNPs,
Thanks for the info! I did a clean download of wine and a clean disc install of ms word. It just seemed strange to me.:confused:

---

