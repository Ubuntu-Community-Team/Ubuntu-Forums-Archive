---
title: "can't find linux-headers-3.8.0-23-generic"
date: 2013-12-18
forum: Virtualisation
---

### Post by kc600 on 2013-12-18
I'm trying to use virtualbox 4.3 from their own ppa's ([https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)).

When i install this, i get:
```
Trying to register the VirtualBox kernel modules using DKMSError! Your kernel headers for kernel 3.8.0-23-generic cannot be found.
Please install the linux-headers-3.8.0-23-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
(This is also the output of 'sudo /etc/init.d/vboxdrv setup')

```

But that headers package can't be installed, is it not in the repo?
```
$ sudo aptitude install linux-headers-3.8.0-23-generic
No candidate version found for linux-headers-3.8.0-23-generic

```

Comically, there is already a module for that kernel version.
```
$ locate vboxdrv
/lib/modules/3.11.0-12-generic/updates/dkms/vboxdrv.ko
/lib/modules/3.11.0-13-generic/updates/dkms/vboxdrv.ko
/lib/modules/3.11.0-14-generic/updates/dkms/vboxdrv.ko
/lib/modules/3.8.0-23-generic/updates/dkms/vboxdrv.ko
```

I'm running Ubuntu 13.10.

---

### Post by howefield on 2013-12-18
You wont find kernel 3.8 headers in saucy repository, I don't think. 13.10 uses the 3.11 kernel.

What is the output of

```
uname -r
```

---

### Post by kc600 on 2013-12-18
For some reason my system was running an old kernel. Running
```
$ sudo aptitude install linux-generic
```
installed the latest kernel and its headers.
I had to reboot to run the new kernel (when uname -a shows 3.11). After that,
```
$ sudo aptitude reinstall virtualbox-4.3
```
worked fine, and i was able to boot up a VirtualBox.

---

