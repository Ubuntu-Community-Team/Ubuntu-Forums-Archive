---
title: "Dependency problems preventing 12.04 LTS upgrade"
date: 2013-05-19
forum: Server Platforms
---

### Post by thugwithyoyo on 2013-05-19
Greetings,

I've been trying to update my Ubuntu 12.04 LTS server by entering first the 

```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

commands into the terminal. The following dependency error prints out before the upgrade completes:

```
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.41.49); however:
  Version of linux-image-generic-pae on system is 3.2.0.43.51.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.41.49); however:
  Version of linux-headers-generic-pae on system is 3.2.0.43.51.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
```

I've also tried to fix the problem using the -f option but the same error still occurs.

I'd greatly appreciate any insights on this.

Thanks!

---

### Post by 2F4U on 2013-05-20
Can you post the complete output of the commands? Is there enough space left to install the new kernel?

---

### Post by thugwithyoyo on 2013-05-31
Thanks for your response.  I discovered that my /boot directory lacked sufficient space to install the new kernel.  After deleting some older kernels stored there, I was able to complete the upgrade.

---

