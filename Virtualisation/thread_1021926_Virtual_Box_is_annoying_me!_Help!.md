---
title: "Virtual Box is annoying me! Help!"
date: 2008-12-26
forum: Virtualisation
---

### Post by macintosh on 2008-12-26
Hello It's macintosh hear having a problem with his Linux Box. He gets this error which is hard to put into words
[IMG]http://img126.imageshack.us/img126/5652/screenshotvboxgtkkd5.png[/IMG]
This is a more detailed error message

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

iConsole? That's funny!

---

### Post by zachalekos on 2008-12-26
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Use this address to download virtual box. then add yourself (your user) to vboxusers group. remember to remove the version you have installed first.

---

### Post by macintosh on 2008-12-26
> **zachalekos said:**
> [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Use this address to download virtual box. then add yourself (your user) to vboxusers group. remember to remove the version you have installed first.

does the OSS version work with vboxgtk? I only use the FOSS version because of that.

---

### Post by albinootje on 2008-12-26
> **macintosh said:**
> does the OSS version work with vboxgtk? I only use the FOSS version because of that.

The error message suggested installing the virtualbox modules that are needed.
You can check whether you have them with :
```

uname -a
dpkg -l|grep -i virtualbox

```

---

### Post by joebeasley on 2008-12-28
Is the module loaded?   /etc/init.d/vboxdrv start

---

### Post by stephanvaningen on 2008-12-29
Possibly this came up after a Ubuntu-update where a new kernel-version was updated/installed. Do this:
 ```
/etc/init.d/vboxdrv setup
```
And you should be up and running, correct?

---

