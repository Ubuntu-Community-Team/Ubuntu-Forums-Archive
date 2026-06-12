---
title: "WARNING: The following packages cannot be authenticated!"
date: 2016-08-23
forum: Security
---

### Post by hari102 on 2016-08-23
Hi,

I tried to install the some debian files from my local repository, while running apt-get upgrade got the following error.

WARNING: The following packages cannot be authenticated!
  bcrelay pptpd
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated

I dont know how to ignore this,Can anyone please assist for this issue.

---

### Post by howefield on 2016-08-23
Is this an Ubuntu installation and packages from the Ubuntu repository ? 

Try

```
sudo apt-key update
```

---

### Post by hari102 on 2016-08-23
No the packages are from my local repository.

---

### Post by ventrical on 2016-08-23
This happens often.. more often than not. It is  (in my experience) an f/p or false positive. It will happen if you ignore  or put aside doing regular update/upgrades .. say ie; trusty or one of the previous not EOL development cycles that have been released. It could also happen if you try to lock a current development version from receiving update/upgrades.

..so you may need to do these..

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --configure -a
sudo apt-get install -f

```


.. you may find you  might have to do it a couple of times to get it lined up correctly.

Regards..

---

