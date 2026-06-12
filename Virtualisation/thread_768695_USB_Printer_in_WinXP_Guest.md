---
title: "USB Printer in WinXP Guest"
date: 2008-04-26
forum: Virtualisation
---

### Post by jwiggs on 2008-04-26
Folks,

   I'm trying to get two different USB printers working in a Windows XP Home installation under VMWare 1.0.5 (downloaded from VMWare site) running under Gutsy.  I can not seem to find a straightforward, step-by-step documentation of the process.  Is there such a document?  What I've pieced together is the following:

1) The USB printer must be connected to the box when the VM is powered on
2) You "present" the USB printer to the guest OS by going into menu "VM -> Removeable Devices -> USB" and setting the check on the device
3) At this point, sometimes WinXP recognizes the device (partially) but I can never seem to get the drivers properly installed so that the device actually works.

   I have a Brother MFC-6800 and an HP Photosmart 3210 All-in-One which I'm trying to get running.  Any pointers to useable documentation would be very much appreciated.

thanks,
Jim

---

### Post by fjgaude on 2008-04-26
Have you done all the following:

In a terminal enter:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Enter your password. We are now in gedit, using root permissions. Uncomment four lines in the file you are looking at starting with line #42. Do this by deleting the "#" in front of each of the four lines so that the lines look like this:

```
       mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Save the file and exit the editor. Next we will edit your fstab using the same gedit program, in a terminal enter:

```
gksudo gedit /etc/fstab
```

Enter your password. Then copy this line and paste it into the end of the file:
```

usbfs /proc/bus/usb usbfs auto 0 0
```

Save the file. Exit the editor. Reboot your computer.

---

### Post by jwiggs on 2008-04-26
> **fjgaude said:**
> Have you done all the following:

In a terminal enter:

```
gksudo gedit /etc/init.d/mountdevsubfs.sh
```

Enter your password. We are now in gedit, using root permissions. Uncomment four lines in the file you are looking at starting with line #42. Do this by deleting the "#" in front of each of the four lines so that the lines look like this:

```
       mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	mount --rbind /dev/bus/usb /proc/bus/usb
```

Save the file and exit the editor. Next we will edit your fstab using the same gedit program, in a terminal enter:

```
gksudo gedit /etc/fstab
```

Enter your password. Then copy this line and paste it into the end of the file:
```

usbfs /proc/bus/usb usbfs auto 0 0
```

Save the file. Exit the editor. Reboot your computer.


Yes, all of this has been put in place.  The VM can see the USB devices, but all attempts to install drivers seem to fail.  I am going to attempt to install the Brother MFC using the parallel port instead, which will make the setup much less convenient, but at least it might work.

thanks,
Jim

---

### Post by fjgaude on 2008-04-26
You mean while you are in VM Windows you are unable to actually have the driver disk load and run?

As I recall, you don't even have to have the USB device turned on to install its driver from disk supplied by the manufacturer.

---

### Post by jwiggs on 2008-04-27
Thanks for the replies; I seem to have worked out a solution.  The steps are very specific and must be done in the proper order:

1. Boot the VM with the printer plugged in, but do *not* present the printer to the VM; that is, go into VM -> Removable Devices -> USB and "uncheck" the printer
2. For a Brother MFC-6800, download the "Windows Printer Wizard" version of the driver and unpack it on the VM
3. Go to the Printers and Faxes control panel and Add a Printer
4. Do *NOT* check the box to "automatically find plug and play printers"
5. Click the "Have Disk" button for the driver and browse to the unpacked driver directory
6. Allow the driver installation to complete and let Windows create the printer
7. Once the new printer is created and the driver is installed, *delete* the new printer
8. No, go to VM -> Removable Devices -> USB and check the box for the printer
9. Windows will loop through the "Found new hardware" routine and create a new printer using the driver we just installed

The same general process works for my HP Photosmart 3200 using the installation CD that came with the printer.

The critical point seems to be to never allow Windows to try to auto-install the device drivers during the process of discovering the new hardware; it will hose things up every time.

---

