---
title: "Installing BLCR"
date: 2011-03-07
forum: Server Platforms
---

### Post by mahmoodn on 2011-03-07
Does anyone here installed BLCR on ubuntu server? I faced a lot of problem installing from source (I am still at configure stage!!).

I have found that BLCR can be installed form standard ubuntu repository ```
blcr-dkms     blcr-modules  blcr-source   blcr-util

```

Is there any difference between installing from source or repository?
```
mahmood@server:boot$ uname -a
Linux server 2.6.32-24-server #39-Ubuntu SMP Wed Jul 28 06:21:40 UTC 2010 x86_64 GNU/Linux
```

---

### Post by windependence on 2011-03-07
Today, there is really no reason to install from source unless you have to. Some will say the binary is faster but in reality you wouldn't know the difference even if it was and since the binary from the repos is compiled for Ubuntu it shouldn't matter anyway. Installing from the repo has advantages like being able to manage your software installs, etc.
 
-Tim

---

### Post by mahmoodn on 2011-03-07
So I installed that from repository and then modprobe the module. However seems that the kernel is crashed while I tested BLCR :(

---

