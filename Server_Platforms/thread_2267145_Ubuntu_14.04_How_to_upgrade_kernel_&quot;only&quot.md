---
title: "Ubuntu 14.04: How to upgrade kernel &quot;only&quot;?"
date: 2015-02-27
forum: Server Platforms
---

### Post by soonthorn.ios on 2015-02-27
Hi,


Currently, we are on 

```
cat /proc/version_signature 
Ubuntu 3.13.0-24.47-generic 3.13.9
cat /etc/issue
Ubuntu 14.04 LTS \n \l



```We'd like to do a kernel upgrade only (not upgrade other applications) to address
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1323165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1323165)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1354234](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1354234)
 
Is this the right command?


```
apt-get install linux-headers-server linux-image-server linux-server



```

Also, do you see any disadvantage or any potential problems of doing just kernel upgrade without upgrade the whole distribution (i.e. apt-get update && apt-get dist-upgrade)?
Thank you for your help!

---

### Post by Habitual on 2015-02-27
I've used ```
# apt-get update
#apt-get install --only-upgrade <package>
``` in the past.

---

### Post by ajgreeny on 2015-02-27
You can also do it with synaptic which allows you to search for ther 3.16 kernels and install whichever one you want, along with the header packages.  That is what I did in precise to upgrade the kernel only, not all the other packages of the hardware-enablement-stack.

The disadvantage of that is the need to manually upgrade the 3.16 at regular intervals as it will not automatically upgrade,though it may do if you install the **linux-generic-lts-utopic** package.

I am sticking with the 3.13 kernel versions which all work very well on my system and my thoughts are:-
"If it ain't broke, don't fix it; if you do fix it and break it, you get to keep the parts"

---

### Post by soonthorn.ios on 2015-03-02
> **ajgreeny said:**
> You can also do it with synaptic which allows you to search for ther 3.16 kernels and install whichever one you want, along with the header packages.  That is what I did in precise to upgrade the kernel only, not all the other packages of the hardware-enablement-stack.

The disadvantage of that is the need to manually upgrade the 3.16 at regular intervals as it will not automatically upgrade,though it may do if you install the **linux-generic-lts-utopic** package.

I am sticking with the 3.13 kernel versions which all work very well on my system and my thoughts are:-
"If it ain't broke, don't fix it; if you do fix it and break it, you get to keep the parts"


Hi ajgreeny,

I do want to stick with the 3.13. So, I just do this?

```
apt-get install linux-headers-3.13.0-46-generic
```

Are there other dependencies I need to explicitly specified? I'm a little confused on what exactly package names I need to install. Is it just linux-headers-<version>-generic or linux-image-<versions>-generic as well?  Thank you for your help.

---

### Post by soonthorn.ios on 2015-03-02
Looks like ```
apt-get install linux-generic
``` is what I need.

---

