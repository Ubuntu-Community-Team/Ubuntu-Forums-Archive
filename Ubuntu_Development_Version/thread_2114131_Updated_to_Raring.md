---
title: "Updated to Raring"
date: 2013-02-09
forum: Ubuntu Development Version
---

### Post by alphacrucis2 on 2013-02-09
I decided to take the plunge and upgrade to the development release. On the first attempt the do-release-upgrade -d script wanted to remove a whole heap of stuff so I aborted the upgrade and tried again a few hours later. On the second attempt the summary of what it was going to looked much more sensible so I let it proceed. The process went through smoothly and here I am using Ubuntu 13.04 dev release.

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu Raring Ringtail (development branch)"
```


 Not much to report at this point as everything seems to be working fine. One thing I did wonder about is the state of the NVIDIA  drivers. I notice software sources still lists six of them plus nouveau. Under 12.10 I was using the one labelled "Experimental (310)" as that was the only one that seemed to work properly. I hope this gets tidied up by the time rr is released.

---

### Post by grahammechanical on 2013-02-09
There is nothing the Ubuntu devs can do about Nvidia drivers. What you see is an improvement made by the Ubuntu devs to give us more choice because of the state of Nvidia drivers.

I have found Nouveau to be acceptable although at the moment I am running Nvidia (proprietary tested). I wanted to experiment to see if I could get a working Nvidia driver.

I never tick Third Party Software when doing an install of Ubuntu. That way I do not get a broken OS on re-boot because a buggy Nvidia driver was installed as part of third party software. Nouveau always gets me to a desktop. I always install Restricted Extras after installation and likewise activate (if I feel like it) the Nvidia driver. I have learned from past errors.

Regards.

---

### Post by rrnbtter on 2013-02-09
Greetings, 
> **grahammechanical said:**
> 
I never tick Third Party Software when doing an install of Ubuntu. That way I do not get a broken OS on re-boot because a buggy Nvidia driver was installed as part of third party software. 


Thanks! I don't have Nvida but I think I will un-tick the Third Party Software anyway. If it can cause problems in one instance then it can be a problem for me. I don't consider myself a serious tester.

---

### Post by alphacrucis2 on 2013-02-09
> **rrnbtter said:**
> Greetings, 


Thanks! I don't have Nvida but I think I will un-tick the Third Party Software anyway. If it can cause problems in one instance then it can be a problem for me. I don't consider myself a serious tester.

The downside is that you will lose performance. The proprietary graphics drivers for Nvidia and AMD cards definitely give better performance.

---

