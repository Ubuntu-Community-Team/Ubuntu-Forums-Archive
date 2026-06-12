---
title: "Sun Virtualbox"
date: 2009-10-02
forum: Virtualisation
---

### Post by Drenriza on 2009-10-02
Im having some trouble with my vitualbox machine, with a linux based server. when i select 
intel pro/1000 MT desktop (82520EM) -> brigded adapter -> eth0
In network i get a 

Failed to start the virtual machine name.
Failed to open/create the internal network 'HostInterfaceNetworking-eth0' (VERR_SUPDRV_COMPONENT_NOT_FOUND).
Failed to attach the network LUN (VERR_SUPDRV_COMPONENT_NOT_FOUND).
One of the kernel modules was not successfully loaded. Make sure that no kernel modules from an older version of VirtualBox exist. Then try to recompile and reload the kernel modules by executing '/etc/init.d/vboxdrv setup' as root (VERR_SUPDRV_COMPONENT_NOT_FOUND).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {0a51994b-cbc6-4686-94eb-d4e4023280e2}

I have tryed to run /etc/init.d/vboxdrv without any changes.

I used eth0 on this virtual machine, in an earlier version of virtual box. But when i updated it to a new version i got this error.

Hope some1 can help me.
Thanks on advance:KS

---

### Post by Perryg on 2009-10-02
It would help to know the version of VirtualBox you are using.  In the mean time you can read this from 2008 and see if it applies to you. 
[http://www.virtualbox.org/ticket/1797](http://www.virtualbox.org/ticket/1797)

---

### Post by Drenriza on 2009-10-07
im using virtualbox-3.0

---

### Post by Perryg on 2009-10-07
> One of the kernel modules was not successfully loaded. Make sure that no kernel modules from an older version of VirtualBox exist. Then try to recompile and reload the kernel modules by executing '/etc/init.d/vboxdrv setup' as root (VERR_SUPDRV_COMPONENT_NOT_FOUND).

Did you uninstall the old version, reboot, and then install the new version as it indicated you do?

---

### Post by Meskarune on 2009-10-26
You do not need to reinstall virtual box, and the message does NOT indicate that you should do so.

after every linux kernel update you should run:

```
sudo vbox_build_module
```

If you get errors about networking and a kernel module not running, then you need to start virtual box's networking module. You can do that by running: 

```
sudo modprobe vboxnetflt 
``` 

and see if that fixes the problem.

---

### Post by chipper_farley on 2009-10-26
You can try running the:

sudo /etc/init.d/vboxdrv setup

as well.  I had a similar problem after installing a new kernel.  Once I did this, everything worked.

---

### Post by drKreso on 2009-11-09
Thanks it helped

---

### Post by Meskarune on 2009-11-15
I'm glad your problem was sorted out. You should mark this topic as "solved" so others can use the information here.

---

