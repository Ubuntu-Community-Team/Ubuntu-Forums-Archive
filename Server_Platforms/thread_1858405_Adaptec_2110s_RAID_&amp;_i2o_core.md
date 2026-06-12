---
title: "Adaptec 2110s RAID &amp; i2o_core"
date: 2011-10-12
forum: Server Platforms
---

### Post by Bluesoft on 2011-10-12
Hi,
 
I have just installed 10.04 LTS Server and dist_upgraded. The architiecture is 32 bit and I have an Adaptec 2110s RAID controller (64 bit but backwards compatible) in PCI slot 1. Initially I found the raid driver was not being loaded but after some searching came across the numerous threads about blacklisting the dpt_i2o driver so that the newer and preferred i2o_core (& block) could claim the appropriate resources. So after blacklisting dpt_i2o in /etc/modprobe.d/blacklist.conf I had more success. However, it was not total success as there appeared to be knock on side effects with the driver of a networking card in PCI 2. 
 
After some headbanging and by chance I looked into the initial ramdisk file:-
 
boot/initrd.img-2.6.33-34-generic-pae
 
and in the image /etc/modprobe.d/blacklist.conf I found ...
 
blacklist i2o_core.
 
So....... this is the exact driver you want loaded... why is it being excluded. I found that once I had amened the image so that it blacklisted dpt_i2o then the RAID and the other PCI card all worked fine..... is this a bug??
 
Many thanks for any insight...

---

### Post by Bluesoft on 2011-10-13
Bump ... anyone? ... was this the wrong forum??

---

