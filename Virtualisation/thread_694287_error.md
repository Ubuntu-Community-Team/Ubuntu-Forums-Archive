---
title: "error"
date: 2008-02-11
forum: Virtualisation
---

### Post by junaid.kollam on 2008-02-11
when i begin to install windows xp in virtual box this error shows
"
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

   help me to solve it

---

### Post by uxe1 on 2008-02-11
go to 
system/ administration /Users and groups
click manage groups
scroll down to vboxusers
and select the users you want to be able to run virtual box.
then log out of your session and log back in.

---

### Post by junaid.kollam on 2008-02-12
problem solved Thanks to ur great help

---

### Post by junaid.kollam on 2008-02-12
now i want to access other partitions of my hard disk and usb drives .please help me

---

### Post by fjgaude on 2008-02-12
Add a line to your fstab file for USB access in your VM:

```
gksudo gedit /etc/fstab
```

Then add this line at the bottom of the file if it doesn't already exist:

```
usbfs /proc/bus/usb usbfs auto 0 0
```

Reboot.

Let us know what happens.

---

### Post by junaid.kollam on 2008-02-12
but how can i access other partition in virtual box

---

### Post by fjgaude on 2008-02-12
I haven't used VBox for months but if memory serves, you go to Devices menu and from there you have the option to select which USBs are active.

---

### Post by junaid.kollam on 2008-02-12
i did not understand ur answer what u mean explain?

---

### Post by fjgaude on 2008-02-12
In VBox menu there is a tab, a menu item, that is called Devices. Click on it and inside there are more clicks possible for the hardware you wish to use.

Okay?

---

### Post by junaid.kollam on 2008-02-12
but there is no option for hard disk accessing

---

### Post by fjgaude on 2008-02-12
Gosh, you access hard disks through the use of Shares.

Maybe there is an information document that can be read. What about this:

[http://ubuntuforums.org/showthread.php?p=4289696#post4289696](http://ubuntuforums.org/showthread.php?p=4289696#post4289696)

Do a google about how to use VBox.

Just got this in:

[http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)

Have fun.

---

### Post by junaid.kollam on 2008-02-12
but there is no option for hard disk accessing

---

