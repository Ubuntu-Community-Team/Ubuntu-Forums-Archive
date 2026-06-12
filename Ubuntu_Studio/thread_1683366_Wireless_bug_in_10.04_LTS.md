---
title: "Wireless bug in 10.04 LTS"
date: 2011-02-07
forum: Ubuntu Studio
---

### Post by windeguy on 2011-02-07
I had a problem with a non-booting system after an updgrade of Ubuntu Studio 10.10 which had been running fine for several months.  I found no way to recover so I started over with a load of 10.04 LTS on my ACER 9410Z. After the install I found that there is a known bug in the kernel that causes problems the BCM4311 wireless chip. The Broadcom wireless support got broken between releases. 

I found this thread and as far as I can tell did everything properly that worked for others down to the application note for recompiling the kernel. 

[http://ubuntuforums.org/showthread.php?t=1390979](http://ubuntuforums.org/showthread.php?t=1390979)

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

I had no luck getting wireless to work.   I am in the middle of a second install of 10.04 LTS. 

Any suggestions?

---

### Post by steveneddy on 2011-02-12
Wireless is not enabled in Ubuntu Studio because it interferes with recording audio - it introduces latency in any audio recording process.

Just plug it into an Ethernet source and update or surf away.

---

### Post by windeguy on 2011-02-13
Thanks. 

I did find a way to enable wireless and did so in the generic kernel. 

I will leave the -realtime kernel alone and only use it with a cable when necessary.

---

