---
title: "Lilo auto installed over grub!"
date: 2006-10-15
forum: Server Platforms
---

### Post by Joespower on 2006-10-15
Hey all,

I use aptitude to grab packages and do updates for a Ubuntu server (Dapper).  Tonight, I was in the aptitude interface and did and update and upgrade of packages.  I wasn't really paying attention, but when everything was downloading, I saw that Dapper had chosen to install LILO and stop using grub!  That was kind of a shock, but I thought there must be a reason.  Then, it told me to run liloconfig, and I did, but it gave me an error complaining that it didn't know how to set up my LVM stuff...

What gives?  Why would LILO even get installed, and why doesn't it setup automatically?  I liked grub damnit!

All I know is that it may have had something to do with the new kernel image...  Any ideas???

---

