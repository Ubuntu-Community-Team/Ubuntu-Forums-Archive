---
title: "USB Memory not detected in virtual Win 7 in Virtual Box"
date: 2011-11-19
forum: Virtualisation
---

### Post by marer13 on 2011-11-19
Hello everyone, 

I need help.
I have installed Virtual Box and managed to install Win 7 virtually.

How can I access USB Memory in virtual Win 7? I tried to connect the USB Memory (Kingston) in Kubuntu and then create a USB filter in Virtual Box, but when I start Win USB doesn't appear inside Windows....

Any help would be greatly appreciated.

---

### Post by jjex22 on 2011-11-20
Have you installed guest additions?

---

### Post by Perryg on 2011-11-23
Actually you don't need the guest additions for USB.  You need to install the Extension Pack if your VirtualBox version is => 4.0 and be sure to place your user name in the vboxusers group on the host and a minimum of log out and in since permissions are changed.

---

### Post by BC59 on 2011-11-23
> **marer13 said:**
> Hello everyone, 

I need help.
I have installed Virtual Box and managed to install Win 7 virtually.

How can I access USB Memory in virtual Win 7? I tried to connect the USB Memory (Kingston) in Kubuntu and then create a USB filter in Virtual Box, but when I start Win USB doesn't appear inside Windows....

Any help would be greatly appreciated.

Installing Win 7 on a virtual machine is not recommended because is very sluggish. You can do everything you like with a usual Win XP installation. Virtualbox can easily recognize the USB on Win XP manipulating the options.

---

### Post by Perryg on 2011-11-23
> **BC59 said:**
> Installing Win 7 on a virtual machine is not recommended because is very sluggish. You can do everything you like with a usual Win XP installation. Virtualbox can easily recognize the USB on Win XP manipulating the options.

Where is this *not* recommended?  I use Windows 7 as a guest and it is as fast as any other virtual machine.

---

