---
title: "how to install virtualbox.tar.gz2"
date: 2008-03-18
forum: Virtualisation
---

### Post by houssam.chahine on 2008-03-18
hi everybody
i am trying to install the virtualbox. the user manual in it explain how to install it but for a debian  file. the file i downloaded from the original website of the virtualbox is a tar.gz. i tried to use the ./configure command but it is not working even the make install command. i am new with ubuntu and i like it very much. please can anyone tell me how to install it step by step.
thank you for your support.

---

### Post by Ub1476 on 2008-03-18
You can search for Virtualbox in add/remove and install it from there.

---

### Post by bodhi.zazen on 2008-03-18
Virtualbox, OSE (Open Source Edition) is in the Ubuntu repositories.

The closed source edition is here :

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI)

Look at the bottom for "Debian systems" for the repositories.

Adding repositories :

[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

Add in the Virtual box repository at the bottom.

The, update and install.

Walkthrough :

[noparse]http://doc.gwos.org/doku.php/doc:office:virtualbox[/noparse]

---

### Post by houssam.chahine on 2008-03-18
i faced this problem when i tried to lunch the virtualbox:

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by bodhi.zazen on 2008-03-18
Try running :

```
sudo apt-get install virtualbox-ose-modules && sudo /etc/init.d/vboxdrv start
```

Sometimes you need to run :

```
/etc/init.d/vboxdrv start
``` a second time.

---

### Post by houssam.chahine on 2008-03-18
Sir, I  did as u told me than i got the following pls can u tell me how to continue
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose-modules is a virtual package provided by:
  virtualbox-ose-modules-2.6.22-14-server 6
  virtualbox-ose-modules-2.6.22-14-generic 6
You should explicitly select one to install.
E: Package virtualbox-ose-modules has no installation candidate

---

### Post by bodhi.zazen on 2008-03-18
Install 

virtualbox-ose-modules-2.6.22-14-generic

I do not know what the "6" on the end means :confused:

---

### Post by houssam.chahine on 2008-03-18
Sir forgive me for bothering u. I did as u told me. i installed the virtualbox-ose-modules-2.6.22-14-generic and i got the following.please can you tell me what to do know

Reading state information... Done
virtualbox-ose-modules-2.6.22-14-generic is already the newest version.
virtualbox-ose-modules-2.6.22-14-generic set to manual installed.
E: Couldn't find package 6

---

### Post by bodhi.zazen on 2008-03-18
Try running the command twice :

```
/etc/init.d/vboxdrv start
/etc/init.d/vboxdrv start
```

If that fails, did you add your user to the vboxusers group ?

And no need to be so formal here ;)

---

### Post by houssam.chahine on 2008-03-18
i used the command /etc/init.d/vboxdrv start i got the following so what is the next step? (sorry am new with ubuntu)

open: Permission denied
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko): Operation not permitted

open: Permission denied
 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

---

### Post by bodhi.zazen on 2008-03-18
LOL, sorry you need sudo

```
sudo /etc/init.d/vboxdrv start
sudo /etc/init.d/vboxdrv start
```

---

### Post by houssam.chahine on 2008-03-18
* Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko): Invalid argument

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

---

### Post by bodhi.zazen on 2008-03-18
can yo post the output of 

```
dmesg | tail
```

---

### Post by houssam.chahine on 2008-03-18
this is the output for the command dmesg | tail :

[13504.968000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[13504.968000] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[13504.968000] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[13506.960000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[13506.960000] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[13506.960000] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[13508.328000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[13508.328000] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[13508.328000] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[13649.692000] sr0: CDROM not ready.  Make sure there is a disc in the drive.

---

### Post by bodhi.zazen on 2008-03-18
OK, that is a little harder ...

We need to edit /boot/grub/menu.lst

```
gksu gedit /boot/grub/menu.lst
```

Scroll down to the boot stanzas, they look like this:

> title Ubuntu, kernel 2.6.17-10-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

On the kernel line, add "nmi_watchdog=0", without quotes, like this :

```
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash nmi_watchdog=0
```

Save and exit gedit.

Reboot and re-try Virtual Box.

Assuming that works, re-edit menu.lst

```
gksu gedit /boot/grub/menu.lst
```

This time, edit the "defoptions" line, add "nmi_watchdog=0" without quotes, like this :

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **nmi_watchdog=0**
```

Save and exit gedit.

Then run this command :

```
sudo update-grub
```

---

### Post by houssam.chahine on 2008-03-19
i did what u told me and i tried to open the virtualbox after that i rebooted i got the following :


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

---

### Post by bodhi.zazen on 2008-03-19
>_<

And, by chance, what happens when you go through :

```
sudo /etc/init.d/vboxdrv start
sudo /etc/init.d/vboxdrv start
```

And, if that fails, dmesg

```
dmesg | tail
```

---

### Post by houssam.chahine on 2008-03-19
* Starting VirtualBox kernel module vboxdrv                                    FATAL: Error inserting vboxdrv (/lib/modules/2.6.22-14-generic/misc/vboxdrv.ko): Invalid argument

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
houssam@houssam-laptop:~$ dmesg | tail
[   51.356000] [fglrx] total      TIM  = 0
[  142.664000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  146.844000] NET: Registered protocol family 17
[  151.780000] NET: Registered protocol family 10
[  151.780000] lo: Disabled Privacy Extensions
[  151.780000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  162.196000] eth0: no IPv6 routers present
[  330.976000] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  330.976000] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  330.976000] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

---

### Post by bodhi.zazen on 2008-03-19
I wonder if there may be a problem with the syntax on /boot/grub/menu.lst. Could you post the contents of that file ?

---

### Post by houssam.chahine on 2008-03-19
/boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied

---

### Post by bodhi.zazen on 2008-03-19
LOL

```
gksu gedit /boot/grub/menu.lst
```

---

