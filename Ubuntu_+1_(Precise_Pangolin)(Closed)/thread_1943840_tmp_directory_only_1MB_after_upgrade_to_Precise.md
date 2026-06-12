---
title: "/tmp directory only 1MB after upgrade to Precise?"
date: 2012-03-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by joehill on 2012-03-20
Since upgrading to Precise, my /tmp directory, which is on my main root partition, which has 300MB free, has a maximum capacity of 1MB. So nothing works, because any time a program tries to write to it, either nothing happens or I get a message saying the partition is full. There's no symlink or anything, so I can't figure out why tmp has a different capacity than any of my other stuff. Any ideas? This is nuts! Thanks.

---

### Post by MacUntu on 2012-03-20
Please post the output of ```
mount | grep "tmp type tmpfs"
```

---

### Post by matt_symes on 2012-03-20
Hi 

/tmp is stored in memory in Ubuntu and not on the hard drive.

EDIT:

Or at least i though it was..... Maybe not. Must remember to double check before posting.

Kind regards

---

### Post by philinux on 2012-03-20
> **joehill said:**
> Since upgrading to Precise, my /tmp directory, which is on my main root partition, which has 300MB free, has a maximum capacity of 1MB. So nothing works, because any time a program tries to write to it, either nothing happens or I get a message saying the partition is full. There's no symlink or anything, so I can't figure out why tmp has a different capacity than any of my other stuff. Any ideas? This is nuts! Thanks.

How big is the root partition? 300 Meg left is not a lot.

---

### Post by joehill on 2012-03-20
Hmm, I rebooted and it's working again. I don't know why rebooting the first time didn't work. Thanks for the suggestions everyone. I'll come back if it happens again.

---

### Post by xebian on 2012-03-20
If you just upgraded there could be a lot of packages in cache.
On a terminal, execute these commands to clean it up

sudo apt-get autoclean 
sudo apt-get clean

---

### Post by dcstar on 2012-03-20
> **joehill said:**
> Hmm, I rebooted and it's working again. I don't know why rebooting the first time didn't work. Thanks for the suggestions everyone. I'll come back if it happens again.

I just read an old thread that said the kernel will create a 1MB /tmp in RAM if the root filesystem has no space. Probably just to get the system to boot up so you can manually make some room for it to run normally.

---

