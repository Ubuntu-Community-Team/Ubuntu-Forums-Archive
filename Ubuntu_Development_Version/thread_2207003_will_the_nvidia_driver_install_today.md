---
title: "will the nvidia driver install today?"
date: 2014-02-21
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-21
And how is it working out now for use?
I like to upgrade once a release hits beta.
But I need the nvidia driver to work.

---

### Post by philinux on 2014-02-21
8600gt and nvidia-current working fine here.

---

### Post by sdowney717 on 2014-02-21
Thanks for that.
What version of the driver are you using?
How did you install it?

I am on 331.38 from xorg-edgers and 12.04

---

### Post by Cavsfan on 2014-02-22
Working fine on this Nvidia Geforce 9800 GT. I have the  Xorg edgers stable PPA installed. 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
Here is what I have installed:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                                  331.38-0ubuntu3                                 amd64        NVIDIA binary driver - version 331.38
rc  nvidia-331-updates                                          331.20-0ubuntu9                                 amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-libopencl1-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
rc  nvidia-libopencl1-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-331                                       331.38-0ubuntu3                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-opencl-icd-331-updates                               331.20-0ubuntu9                                 amd64        NVIDIA OpenCL ICD
rc  nvidia-persistenced                                         331.20-0ubuntu1~xedgers~trusty1                 amd64        Load the NVIDIA kernel driver and create device files
ii  nvidia-prime                                                0.5.7                                           amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                             331.38-0ubuntu1~xedgers~trusty1                 amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by philinux on 2014-02-23
> **sdowney717 said:**
> Thanks for that.
What version of the driver are you using?
How did you install it?

I am on 331.38 from xorg-edgers and 12.04

nvidia-current from additional drivers.

I always run a vanilla install for testing.

---

### Post by sdowney717 on 2014-02-24
I installed xorg-edgers ppa for 331 driver.
A few new things I had to learn with multiple monitors, you must use display properties as nvidia-settings dont apply.

So far it feels good this 14.04

---

