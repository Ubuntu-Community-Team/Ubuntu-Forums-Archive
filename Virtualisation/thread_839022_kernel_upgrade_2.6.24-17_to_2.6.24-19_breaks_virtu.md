---
title: "kernel upgrade 2.6.24-17 to 2.6.24-19 breaks virtualbox"
date: 2008-06-24
forum: Virtualisation
---

### Post by fethio on 2008-06-24
Hello

virtualbox gives the following error when i boot with my new 2.6.24-19 kernel. 

[INDENT]
Failed to start the virtual machine ...

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).

Result Code: 0x80004005
Component: Console
Interface: IConsole {1dea5c4b-0753-4193-b909-22330f64ec45} [/INDENT]

when i boot with 2.6.24-17, vbox works.

help is appreciated...

---

### Post by hopelessone on 2008-06-24
```
sudo /etc/init.d/vboxdrv setup 
```

---

### Post by fethio on 2008-06-24
thanks. here's the output of your suggestion

> fethi@desktop-A709:/boot$ sudo /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv
 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.


---

### Post by zgornel on 2008-06-24
'setup', not 'start' :D

---

### Post by negativ on 2008-07-28
> **zgornel said:**
> 'setup', not 'start' :D

That gives me:

> 
:~$ sudo /etc/init.d/vboxdrv setup
* Usage: /etc/init.d/vboxdrv {start|stop|restart|status}
:~$


---

### Post by Maitar on 2008-12-16
you don't have the setup option because you're using an old version of virtualbox. (probably 1.5.6 or so) The version available in the ubuntu/kubuntu repository is an older version, so don't bother waiting for an update. The current version is 2.0.6
Go to virtualbox.org and get the latest version. Install instructions for the open source edition are on the site (at the bottom of the downloads page) if you don't know how to do it. Follow them carefully and you'll have no trouble. Once updated it should work fine. Or you can use the binaries for the closed source version if that suits you.

---

### Post by hongri1998 on 2008-12-17
Manually operated **[ball valve](http://www.valvesupplier.net/petro-valve.htm)** can be closed quickly and thus there is a danger of water hammer. Some ball valves are equipped with an actuator that may be pneumatically or motor (electric) operated. These [ball valves]("http://www.valvesupplier.net/petro-valve.htm") can be used either for on/off or flow control.

---

