---
title: "virtualbox problems"
date: 2008-04-01
forum: Virtualisation
---

### Post by Pevichaey5 on 2008-04-01
hi

i have a slight problem, when i try to start windows xp (not even installed yet) i get this message

```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```


if i follow the instructions i get this message

root@ubunu154:/home/toby# /etc/init.d/vboxdrv start
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
root@ubunu154:/home/toby# 

any help

cheers

---

### Post by zvacet on 2008-04-01
From synaptic install virtualbox-ose-modules (install generic one).After that type in terminal

```
sudo /etc/init.d/vboxdrv start
```

---

### Post by Pevichaey5 on 2008-04-01
yea i tried that many times, but i get the same message, i haven't however installed the server one, is there a chance it could work if i install it?

cheers

---

### Post by jnbek on 2008-04-01
So what's the output from dmesg?

---

### Post by Pevichaey5 on 2008-04-02
I did try that last night, but this is no longer relevent, i have since formatted and reinstalled virtualbox is working as it should

i'm assuming because i was running ubuntu studio 7.10, that was it wasn't working

cheers

---

