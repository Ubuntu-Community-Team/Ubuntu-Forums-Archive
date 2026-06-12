---
title: "PSA: NVidia users, before you apt autoremove"
date: 2021-11-23
forum: Ubuntu, Linux and OS Chat
---

### Post by LokiScarlet on 2021-11-23
Note: I'm not looking for support for this, just want to make others aware.

APT on Ubuntu currently labels many NVidia packages auto-removable that are components of your installed NVidia driver. If you're cleaning up your packages with autoremove, make sure to reinstall your NVidia driver before rebooting. In my experience, for example, it removes everything but the xorg driver as a consequence of removing the following packages:

```
libaccinj64-11.3 libcub-dev libcublas11 libcublaslt11 libcudart11.0 libcufft10 libcufftw10 libcupti-dev libcupti-doc libcupti11.3 libcurand10 libcusolver11 libcusolvermg11 libcusparse11 libnppc11 libnppial11 libnppicc11 libnppidei11 libnppif11 libnppig11 libnppim11 libnppist11 libnppisu11 libnppitc11 libnpps11 libnvblas11 libnvjpeg11 libnvrtc-builtins11.3 libnvrtc11.2 libnvtoolsext1 libnvvm4 libthrust-dev libvdpau-dev node-html5shiv nsight-compute nsight-compute-target nvidia-cuda-gdb nvidia-cuda-toolkit-doc
```

Some of these packages might not be NVidia-specific, I haven't checked all of them, but after autoremoving, installing the driver again, and doing a dry run of autoremove, these came up.

My best advice for those of us who might need to use autoremove at some point, is to manually install these packages so they won't be marked as auto-removable.

---

### Post by TheFu on 2021-11-23
I appreciate the heads up.  I autoremove almost every week, after patching.  I don't patch daily, so perhaps I miss the worse packaging mistakes?  Come Saturday, I'll pay attention.

---

### Post by poorguy on 2021-11-24
I've had some problems with the Nvidia proprietary graphics driver and prefer to not use it. 
The open source nouveau graphics driver seems to work good for my old Frankenstein desktops.

---

### Post by doc taz on 2021-11-26
This is great advice! I don't feel the need to autoremove anything, as I have a huge 2 TB M.2 SSD as my primary drive. Not everyone has this size, so this advice is helpful. Not autoremoving does have its benefits... nearly eliminates instances of dependency hell.

---

### Post by TheFu on 2021-11-26
> **doc taz said:**
> This is great advice! I don't feel the need to autoremove anything, as I have a huge 2 TB M.2 SSD as my primary drive. Not everyone has this size, so this advice is helpful. Not autoremoving does have its benefits... nearly eliminates instances of dependency hell.

Dependencies get broken when packages are manually installed, but not updated. This easily can lead to a 2 yr old manual package holding lots of fixed packages back on a system, leading to old bugs and unfixed security issues.

The key for whether someone should remove old packages is dependent on the size of /var/apt/ and whether they install .deb files manually that have dependencies that aren't x.y.z+ ... some package creators don't let newer, dependent, packages be installed for whatever reason. Sometimes this is good to prevent breakage and sometimes it is ignorance about package versioning standards. Everyone was new at some point and everyone makes mistakes. APIs shouldn't change when 'z' changes, provided x.y do not change.  Often, even when 'y' changes, only new APIs are added and older APIs are left alone.  Only someone reading the code and looking through the package dependencies carefully would be able to tell.

---

### Post by mastablasta on 2021-11-29
this happens ofrm time to time and you just reinstall nvidia proprietary driver. it happened once on my kids PC so far.

---

### Post by TheFu on 2021-11-29
Just wanted to report that my weekly patching on a system with an AMD 2600 w/ nvidia 1030 didn't have any issues. No new nvidia drivers were installed, so something else was happening ... it wasn't just normal updates.  

That system runs 5.4.0-90-generic and has been up
```
$ uptime 
 10:16:44 up 14 days, 22:32,  5 users,
```
It is fairly stable.

OTOH, it doesn't use CUDA or bleeding edge kernels, which may be the difference.  Another system here, without nVidia, is running a very new kernel and it has been stable too - also up 14 days now.

---

### Post by mastablasta on 2021-11-30
in my kids case it happened when driver was bumped up from ver. 430 to 450. i only saw it once. it could be it patched the driver but not the kernel at the same time. in any case it was a fast reinstall through additional drivers. haven't seen anything similar since then.

---

