---
title: "[Elementary OS] Disk space full"
date: 2014-08-07
forum: Ubuntu/Debian BASED
---

### Post by tfernandes on 2014-08-07
Hi all,

i'm running elementary OS (DEB Version of ubuntu) 

my drive always shows diskspace full although there is enough space. 
I'm a newbie to linux so can't understand much i downloaded diskutility but it only shows partition information and doesnt show usage details.

plz advise how to get usage details and then free some files if required.

screens below

The 55GB partition is the primary on which i usually downloaded torrents. But as i'm getting space error i have to manually copy the downloaded files to the other 67 GB partition. Even my dropbox sync is on the 55gb partition but giving me low disk space error.

---

### Post by coffeecat on 2014-08-07
*Thread moved to **Other Operating Systems and Projects**.*

Open a terminal and post the output of this command:

```
df -h
```

That will show how much each mounted partition is used. From there someone should be able to help you free up the space.

---

