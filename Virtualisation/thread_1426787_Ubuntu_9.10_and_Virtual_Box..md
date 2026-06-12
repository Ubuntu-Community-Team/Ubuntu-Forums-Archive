---
title: "Ubuntu 9.10 and Virtual Box."
date: 2010-03-10
forum: Virtualisation
---

### Post by Dyffo on 2010-03-10
I have Ubuntu 9.10 and have installed Virtual Box  3.09 OSE.( Guest additions are on an ISO image )

I am installing XP professional, but cannot get either Guest Additions or USB to work.

When I press the Add Guest Additions tab nothing happens, and the USB I cannot locate.

---

### Post by mkvnmtr on 2010-03-10
I use the latest virtual box from the sun site on 9.04. I have installed XPpro twice. If I remember correctly it offered me the chance to run the installation script. If not you might need to open the guest additions and right click on the autorun.sh and see it it ofers the option to run.
I would recomend uninstalling the older virtual and reinstalling the lattest . It will give you better usb support

---

### Post by Beowulf.1000 on 2010-03-11
I just did exactly what you are trying to do, yesterday, and it worked smooth. I installed Ubuntu 9.10 a few days ago, then added VB using the package manager, then installed WinXP Professional. Then used synaptic package manager again to hunt for guest addition package for VB and added that package. Then fired up VB and added Guest Addition; I don't recall if first I had to start up WinXP, I think you might do that first, then with virtual WinXP running in VB, go into the VB menu and choose to add a guest addition. Really nice, as the mouse just smoothly goes between Linux and WinXP, none of that weird capturing of the mouse confusion.

> **Dyffo said:**
> I have Ubuntu 9.10 and have installed Virtual Box  3.09 OSE.( Guest additions are on an ISO image ) I am installing XP professional, but cannot get either Guest Additions or USB to work.
When I press the Add Guest Additions tab nothing happens, and the USB I cannot locate.

---

### Post by Dyffo on 2010-03-11
Hi thanks for responses, I have Installed latest V Box from the Sun Site, but now get the following error message - any ideas please.


Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

---

### Post by tacantara on 2010-03-11
> **Dyffo said:**
> Hi thanks for responses, I have Installed latest V Box from the Sun Site, but now get the following error message - any ideas please.


Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

To install the DKMS package, open a terminal window and enter the following command:

```
sudo apt-get install dkms
```

Once that's installed, you can reinstall the kernel module as described in the error message by entering this command in the terminal:

```
sudo /etc/init.d/vboxdrv setup
```

Once you've completed these steps, you should be able to open VirtualBox and set up your VM.

---

### Post by Dyffo on 2010-03-11
> **tacantara said:**
> To install the DKMS package, open a terminal window and enter the following command:

```
sudo apt-get install dkms
```

Once that's installed, you can reinstall the kernel module as described in the error message by entering this command in the terminal:

```
sudo /etc/init.d/vboxdrv setup
```

Once you've completed these steps, you should be able to open VirtualBox and set up your VM.

O.K- Have got the DKMS but not Vbox Drv - see below :-

mike@mike-desktop:~$ sudo /etc/init.d/vboxdrv setup
sudo: /etc/init.d/vboxdrv: command not found
mike@mike-desktop:~$

---

### Post by Hero of Time on 2010-03-11
Reinstall the PUEL version you got from the website. See [VirtualBox FAQ](http://forums.virtualbox.org/viewtopic.php?t=8669) for more information about your error. It also handles lots of other questions you might be interested in.

---

### Post by Dyffo on 2010-03-12
> **Hero of Time said:**
> Reinstall the PUEL version you got from the website. See [VirtualBox FAQ](http://forums.virtualbox.org/viewtopic.php?t=8669) for more information about your error. It also handles lots of other questions you might be interested in.

Thanks Guys - All up and running at last !:D

---

### Post by Beowulf.1000 on 2010-03-12
So you installed PUEL Vbox? Solved the issue? 
As a non-PUEL user so far, would you be able to comment on the USB access issue, i.e. I have heard PUEL gives seemless access to USB? Can you hot swap USB devices, like an mp3 player USB cable, midi keyboard usb cable (okay you might not have that, but I will need to get that working at some point), other.

> **Dyffo said:**
> Thanks Guys - All up and running at last !:D

---

### Post by Dyffo on 2010-03-12
> **Beowulf.1000 said:**
> So you installed PUEL Vbox? Solved the issue? 
As a non-PUEL user so far, would you be able to comment on the USB access issue, i.e. I have heard PUEL gives seemless access to USB? Can you hot swap USB devices, like an mp3 player USB cable, midi keyboard usb cable (okay you might not have that, but I will need to get that working at some point), other.

Hi , All I can tell you so far is that the USB is now as versatile as it was with Ubuntu,& Windows Xp - I can perform any function that requires USB support Printers, Cameras, Ext Hard Drives etc- will keep you posted as to progress. The link below did it all for me.


[http://ubuntuforums.org/showthread.php?t=1074160](http://ubuntuforums.org/showthread.php?t=1074160)

If I can be of more help I will try to assist.

---

