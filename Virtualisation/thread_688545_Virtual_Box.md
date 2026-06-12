---
title: "Virtual Box"
date: 2008-02-05
forum: Virtualisation
---

### Post by Benbow on 2008-02-05
I am struggling to install virtual box but the following message constantly appears??

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the 
virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by wolfen69 on 2008-02-05
did you install the .deb file from the virtualbox website? if you need the ose modules, they are available in synaptic.

---

### Post by bodhi.zazen on 2008-02-05
First add the ose module :

```
sudo apt-get virtualbox-ose-modules-`uname -r`
```

Note those are bac tics ` and NOT single quotes '

Then, add you user to the Vobxusers group, log out and back in, should be good to go.

---

### Post by Benbow on 2008-02-05
Any ideas what this means?

VERR_FILE_NOT_FOUND)

---

### Post by bodhi.zazen on 2008-02-05
VERR = VirtualBox ERRor message

FILE_NOT_FOUND = File not found

:twisted:

---

### Post by Jaymac on 2008-02-09
I installed it through synaptic and got this message on installation...

```
Setting up virtualbox-ose-modules-2.6.22-14-generic (6) ...
 * Starting VirtualBox kernel module vboxdrv                                    chown: `:vboxusers': invalid group

 * Cannot change owner vboxusers for device /dev/vboxdrv.

```

I manually created the group vboxusers afterwards; how to I give the group ownership of /dev/vboxdrv..?

I tried chown vboxusers, but it seems that only works for users and not groups...

When I try to start the virtual machine I get the error:

```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).
```

I believe this is related to my initial installation issue...

---

### Post by virtualXTC on 2008-03-01
In kubuntu I'd use the "system settings", "users management"  widget.
However given you are probably using gnome, the widget for it is probably either non-existant or buried though in a convoluted hierarchy of unintuitive menus.  Therefore, you should try the 'chgrp' comand.  ;-)

---

