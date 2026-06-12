---
title: "TVheadend Server"
date: 2019-07-14
forum: Server Platforms
---

### Post by udbytossen on 2019-07-14
Hi Guys. 
Normally I've been running debian for several years - but using now Ubuntu for several servers. Allthough I have an issue on my TVheadendserver. After running MythTV for several i switched over to TVheadhend
 My setup is
Shuttle XPC with Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz 
16GB RAM and 2 x SSD disk 
TBS 6985QUAD tuners 

Since my PCI is a TBS Tunercard - I'm running lowlatency kernel with the TBS drivers. and here its: 

3days ago I did a apt upgrade - and it totally crashed my setup. So i did reinstall on server 16.04 again - as described in this guide [https://tvheadend.org/projects/tvheadend/wiki/GoodKernelAndDriver](https://tvheadend.org/projects/tvheadend/wiki/GoodKernelAndDriver)

I'm wondering if its possible to upgrade the server to 18.04LTS if its possible to run a lowlatency kernel since I really had a performance boost with running with this lowlatency kernel. 
So I'm thinking about dooing a "do-release-upgrade" but can any experts give a hint if I loose performace on TVtunercard - when running 18.04 instead of 16.04 ???

---

