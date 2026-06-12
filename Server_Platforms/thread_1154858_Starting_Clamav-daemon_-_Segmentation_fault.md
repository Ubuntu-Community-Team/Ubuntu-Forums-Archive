---
title: "Starting Clamav-daemon - Segmentation fault"
date: 2009-05-10
forum: Server Platforms
---

### Post by satimis on 2009-05-10
Hi folks,


OpenVZ
guest(VE) - OS, Ubuntu 8.04
Clamav-daemon


On running;

root@vz2:/# /etc/init.d/clamav-daemon start```

 * Starting ClamAV daemon clamd                                                  
LibClamAV Warning: ***********************************************************
LibClamAV Warning: ***  This version of the ClamAV engine is outdated.     ***
LibClamAV Warning: *** DON'T PANIC! Read http://www.clamav.net/support/faq ***
LibClamAV Warning: ***********************************************************
LibClamAV Error: cli_realloc(): Can't re-allocate memory to 19784 bytes.
realloc_problem: Cannot allocate memory
LibClamAV Error: cli_ac_addpatt: Can't realloc ac_pattable
LibClamAV Error: cli_parse_add(): Problem adding signature (1).
LibClamAV Error: Problem parsing database at line 56181
Segmentation fault			[fail]

```

root@vz2:/# ls /tmp/```

clamav-a0d562c1d717bbd7eddc575952c444a4

```

root@vz2:/# ls /tmp/clamav-a0d562c1d717bbd7eddc575952c444a4/```

COPYING  main.db  main.fp  main.hdb  main.info  main.mdb  main.ndb  main.zmd

```


root@vz2:/# cat /etc/apt/sources.list```

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe  #
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe  #

```

Please advice how to fix the problem?  TIA


B.R.
satimis

---

### Post by ikonia on 2009-05-10
this may sound like an obvious cop out, but trying running it on a physical machine, OpenVZ seems to have a few issues as a virtualzation host (looking at generic forum posts) 

are you using a generic ubuntu install on it, or an install that someone created for openVZ ?

---

### Post by satimis on 2009-05-10
> **ikonia said:**
> this may sound like an obvious cop out, but trying running it on a physical machine, OpenVZ seems to have a few issues as a virtualzation host (looking at generic forum posts) 

are you using a generic ubuntu install on it, or an install that someone created for openVZ ?
Hi ikonia,

I created VE (the guest) using OpenVZ template.


B.R.
satimis

---

### Post by ikonia on 2009-05-10
without being a wimp - I'd call that out as the problem straight away until proven else where.

The only reason I call this out straight away is due to the ammount of people who are sold "virtual machine" hosting and the hosts either use modified images, or ubuntu installs that they have mashed up and just cloned

Good example is to always check the kernel version.

These images cause so many problems with incompatible packages, memory issues etc etc, contact the image proivder first see if they have these problems or the ability to debug them

---

