---
title: "USB scanner not being found by VirtualBox"
date: 2008-05-08
forum: Virtualisation
---

### Post by Robbyx on 2008-05-08
I installed Win2K on a spare disk to check if the scanner is working and much to my surprise it is working properly. I was very close to throwing the scanner away but decided to test it first on a pure windows machine.

From within VB using win2k as the guest and Hardy H as the host the scanner is not operable. The scanner is a USB scanner from Visioneer: Strobe XP 450.

Following advice elsewhere I tried the following:

> robin@robin:~$ sudo gedit /etc/udev/rules.d/40-permissions.rules


I altered the mode setting in following area:

> # USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", \
					MODE="0666", GROUP="dialout", GROUP="vboxusers" 
# was MODE="0660", GROUP="dialout", GROUP="vboxusers" 
LABEL="usb_serial_end"

The change above has not made any difference. 

What should happen is that when  I install the driver and then plug in the usb cable Win2k should complete the installation automatically. Nothing happens.


Could I please have some help to get this scanner to work?

Robin

---

### Post by Whiffle on 2008-05-08
I'm pretty sure you need to add a line to /etc/fstab similar to:

none                    /proc/bus/usb   usbfs   devgid=102,devmode=664   0       0

Search it first though, thats from mine, which is running Arch and not Ubuntu.

---

### Post by Robbyx on 2008-05-08
My fstab has this in it and it made no difference to the scanner:

none /proc/bus/usb usbfs defaults,devmode=0666 0 0 

Robin

---

### Post by Whiffle on 2008-05-08
Okay, is virtualbox seeing it, and is USB enabled for that virtual machine?  Should look something like this:

---

### Post by Robbyx on 2008-05-08
I do not recognise the screen shot. Is it taken from within windows? I am using win2k.

In the details for the VM it states USB Device filters 0(0 active)

The scanner is not showing in the Win2k Scanner control icon within the control panel.

Within the device manager of windows it is not showing a separate entry under the USB controllers for the scanner.

Robin

---

### Post by Whiffle on 2008-05-08
Ok, what you need to do is go to the Virtualbox Virtual Machine manager, click on the virtual machine you want to add usb support to, and then on the right side click "USB".  This will bring up the screen i posted above.  On the right side there is a little icon with a USB plug and a green plus sign, click that, and it should bring up a little list of USB devices that are connected, click the name of the device and a filter will be added for it.  

Then, in the "Devices" menu on the running virtual machine, there is an item for USB devices, when you mouseover that it should show your scanner there, and then make sure it has a check mark next to it if you want to use it.

---

### Post by Robbyx on 2008-05-08
Under  VB VM's settings for the USB:

USB controller and USB 2 controller are both enabled.

There is nothing showing in the USB devices filter. I clicked on the add new filter button, but it does not auto fill and I do not know what to put in the boxes that are likely to work.

R

---

### Post by Robbyx on 2008-05-08
I have just spotted another button that has enabled me to choose an existing device. My scanner is now showing as a usb device. There is no port or serial number auto completed.

---

### Post by Robbyx on 2008-05-08
On loading the VM and running the scanner program it says 

Failed to initialise scanner. 

I am going to reinstall the scanner software.

R

---

### Post by Robbyx on 2008-05-08
> **Robbyx said:**
> On loading the VM and running the scanner program it says 

Failed to initialise scanner. 

I am going to reinstall the scanner software.

R


I am very pleased to say that I now have it working. Thank you.

R

---

### Post by dsjstc on 2011-01-09
For others stumbling onto this thread: frequently the problem is a bug in the VB's ECHI support.  Just go into the VM's USB settings and disable EHCI (usb 2.0) support.

[http://forums.virtualbox.org/viewtopic.php?f=6&t=18569](http://forums.virtualbox.org/viewtopic.php?f=6&t=18569)

---

