---
title: "[SOLVED] VirtualBox error Please help"
date: 2008-09-01
forum: Virtualisation
---

### Post by nowin4me on 2008-09-01
Hello all,

I get the following error when I try and start up a virtual machine:

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

I would really like to start a virtual machine so I can test out Ubuntu 8:10 BETA or ALPHA (Not sure which).

Why would I want to do that?
The more errors/bugs I/we find now the less errors/bugs there will be in the final version.

You can download Ubuntu 8:10 BETA or ALPHA (Not sure which) here.
[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

I am doing this because I love Ubuntu and the community.

You help me I will help you.

Thanks

---

### Post by lazyart on 2008-09-01
do what it's telling to you do:```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by overdrank on 2008-09-01
moved :) 
and lazyart beat me to it :)

---

### Post by nowin4me on 2008-09-01
> **lazyart said:**
> do what it's telling to you do:```
sudo /etc/init.d/vboxdrv setup
```


Your a genius Thanks and have a thanks

---

