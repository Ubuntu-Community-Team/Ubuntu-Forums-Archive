---
title: "Disabling the Hpt366 module"
date: 2008-05-29
forum: Server Platforms
---

### Post by MasterMaxus on 2008-05-29
Hi People,

I was wondering if anyone knew how to disable the hpt366 module? I need to diable it to be able to use a custom compiled hpt374 module from highpoint, the two modules are conflicting with each other.  

I have added the following to my etc/modprobe.d/blacklist

blacklist hpt366

rebooted the machine but the module is still being loaded:

lsmod | grep hpt366
hpt366                 25984  0 [permanent]
ide_core              143768  3 ide_disk,hpt366,atiixp

any ideas how to fix it?

I'm using Ubuntu 8.04 LTS Server Distro.

Thanks in Advance
Maxus

---

### Post by quelx on 2008-05-29
edit **/etc/initramfs-tools/initramfs.conf**

change **MODULES=most** to **MODULES=list**

edit **/etc/initramfs-tools/modules** with a list of modules you want to use (**lsmod** the active system to get your list) including your custom module

then 

```
sudo update-initramfs -u
```

---

### Post by MasterMaxus on 2008-05-29
Thanks quelx,

That worked perfectly, only change i had to make was instead of:

[PHP]
sudo update-initramfs
[/PHP]

I needed to do:

[PHP]
sudo update-initramfs -u
[/PHP]

How will this affect installing new applications and so on, I assume now all the modules will have to be hand managed?

Thanks
M

---

### Post by quelx on 2008-05-29
Only if you change the hardware will you need to know the drivers and which modules to load.  Kernel updates use **update-initramfs** so as long as you have **MODULES=list** I can't think of any software updates that would hurt the install (maybe an update of **initramf-tools** itself)

---

