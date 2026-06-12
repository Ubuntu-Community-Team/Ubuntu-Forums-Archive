---
title: "Boot Only in Recovery mode"
date: 2012-03-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mr best buy on 2012-03-11
After a year of operaiion, my Operating system will only boot in recovery mode.  In the nornal mode the screen  flickers with lines of words I cannot read because they go by so fast.  
I reinstaLLED TWICE AND loaded version 12.4 on this computer and the same thing happens.  
When I reinstall I ask it to earse the old and install the new. 
I have windows 7 on a different partition and it works just fine...Please help

---

### Post by howefield on 2012-03-11
Thread moved to the "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by hette on 2012-03-11
I think this is the bug that affects you: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/936667]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/936667")
There is a patched upstart package available which solved the problem for me. See post #14 in the bug report.

---

