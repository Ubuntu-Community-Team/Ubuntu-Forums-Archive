---
title: "Retained packages in Beta 1"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by wgarcia on 2012-09-09
I upgraded to Ubuntu 12.10 Beta 1 on Friday, and I have had the following retained packages for two days:

libunity-core-6.0-5 linux-headers-generic linux-image-generic oss-compat unity unity-common unity-greeter unity-services

Do you know if it is safe to force the upgrade of these packages? (I mean with "sudo apt-get install ...")

---

### Post by ventrical on 2012-09-09
I got the same thing, even with current installs.  From experience they say to ride the storm out. :)

---

### Post by zika on 2012-09-09
> **wgarcia said:**
> I upgraded to Ubuntu 12.10 Beta 1 on Friday, and I have had the following retained packages for two days:

libunity-core-6.0-5 linux-headers-generic linux-image-generic oss-compat unity unity-common unity-greeter unity-services

Do you know if it is safe to force the upgrade of these packages? (I mean with "sudo apt-get install ...")Did You try```
sudo apt-get dist-upgrade
```?
Of course, with all the caution that is always needed for "partial" upgrade...

---

### Post by wgarcia on 2012-09-09
Thanks ventrical and zika, I always forget about "dist-upgrade". Well, if it tells me that it will remove all my desktop I promise I will not press "accept".

---

### Post by wgarcia on 2012-09-09
All good, 

```
sudo apt-get dist-upgrade
```

pulled the additional packages and did not want to remove anything funny.

---

