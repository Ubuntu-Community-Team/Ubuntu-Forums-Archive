---
title: "Kernel 3.13-rc1 is out"
date: 2013-11-22
forum: Ubuntu Development Version
---

### Post by paul_in_london on 2013-11-22
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc1-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.13-rc1-trusty/)

Installed the debs, booted the new kernel, reinstalled nvidia-304.

The nvidia module built ok, but I was stuck in low graphics mode because the nvidia module didn't load properly.

From /var/log/kernel.log:

```
...Nov 22 22:54:12 trusty-64 kernel: [   23.421709] tg3 0000:3f:00.0 eth0: Flow control is off for TX and off for RX
Nov 22 22:54:23 trusty-64 kernel: [   34.674719] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)
Nov 22 22:54:23 trusty-64 kernel: [   35.020818] nvidia: Unknown symbol acpi_os_wait_events_complete (err 0)
```

So back to nouveau for now.

```
paul@trusty-64:~$ uname -a
Linux trusty-64 3.13.0-031300rc1-generic #201311221535 SMP Fri Nov 22 20:36:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
paul@trusty-64:~$
```

---

### Post by sammiev on 2013-11-22
Thanks paul

```
sam@samL650:~$ uname -r
3.13.0-031300rc1-generic
sam@samL650:~$
```

---

### Post by Milos_SD on 2013-11-25
To get Nvidia drivers working, take a look at my solution here:
[https://devtalk.nvidia.com/default/topic/644906/linux/331-20-on-3-13-rc1-kernel/](https://devtalk.nvidia.com/default/topic/644906/linux/331-20-on-3-13-rc1-kernel/)

---

### Post by slickymaster on 2013-11-28
Well, with me it's the same old mess with the VBoxLinuxAddittions, but any way, it's running smoothly

```
slickymaster@VirtualBox:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Trusty Tahr (development branch)
Release:	14.04
Codename:	trusty
3.13.0-031300rc1-generic
```

---

### Post by Shiba on 2014-01-08
> **Milos_SD said:**
> To get Nvidia drivers working, take a look at my solution here:
[https://devtalk.nvidia.com/default/topic/644906/linux/331-20-on-3-13-rc1-kernel/](https://devtalk.nvidia.com/default/topic/644906/linux/331-20-on-3-13-rc1-kernel/)

Already tried but it doesn't work for me. X crashes and the system freezes.

---

### Post by Yahoé on 2014-01-08
3.13.0-1-generic got pushed from the official repository but the display was just unbearable for me on a system with a Radeon HD 4200 series, bad resolution, dark, colours totally off. Switched back to 3.12.0-7-generic.

---

