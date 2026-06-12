---
title: "The swap partition is not being used"
date: 2010-04-19
forum: Server Platforms
---

### Post by E=mc2 on 2010-04-19
Hi folks,

I recently installed Ubuntu Server, the 8.04LTS release, on my dad's computer which, for the time being, has to dual-act as both a server and a desktop. Will be running solely as a server pretty soon, though. Anyway - since I was down on the budget and the project I put up the server for is still in a development phase and not worth to invest serious money in (at this stage), it has to run on a computer with the following hardware configuration (I left out the non-important parts):
```

Intel Celeron 2.2 Ghz
~500 MB of DDR 333MHz RAM

```
It has 80 or so GBs of disk space, so I went for the low-mem, high-disk scenario and created a swap partition of 1,5 GB. However, I can notice that is rarely even used! I have set the vm.swappiness parameter to 95 but my swap partition is still not being used, even when the memory usage goes up to 90%. I saw it being used once, but only when the needed memory size exceeded 500.

Does anybody know how to force Ubuntu Server to use the swap partition?

---

### Post by trundlenut on 2010-04-19
If you aren't using all the available memory why would you want to force the machine to use swap?  Surely it will just slow things down and you'l  just end with more memory you aren't using anayway.

Having a GUI will use more memory than most other things, one of my servers is running LAMP, joomla, webmin and Dell OMSA and that only uses about 200Mb of ram out of 2Gb available.

---

### Post by Vegan on 2010-04-19
I prefer to cram it with RAM and try to not use a /swap at all.

---

