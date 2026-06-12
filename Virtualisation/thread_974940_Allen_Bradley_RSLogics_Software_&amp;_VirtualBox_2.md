---
title: "Allen Bradley RSLogics Software &amp; VirtualBox 2.04"
date: 2008-11-08
forum: Virtualisation
---

### Post by lkraemer on 2008-11-08
If you are a Plant's Shift Electrician, Support Technician, or Engineer, and have been wanting to get the Allen Bradley RSLogics 5, RSLogics 500, or RSLogics 5000 software running on a Linux Laptop with VirtualBox, I have it working on Ubuntu 8.04LTS.


**USB Information**
[http://www.informit.com/articles/article.aspx?p=1235054&seqNum=2](http://www.informit.com/articles/article.aspx?p=1235054&seqNum=2)

[https://help.ubuntu.com/community/VirtualBox#USB](https://help.ubuntu.com/community/VirtualBox#USB)

Furthermore, your user must be able to access /proc/bus/usb/*

Since Gutsy, /proc/bus/usb is not mounted by default. You need to edit /etc/init.d/mountdevsubfs.sh and uncomment the following lines:

```

        #
        # Magic to make /proc/bus/usb work
        #
        mkdir -p /dev/bus/usb/.usbfs
        domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
        ln -s .usbfs/devices /dev/bus/usb/devices
        mount --rbind /dev/bus/usb /proc/bus/usb

```

In order to give users in the vboxusers group write permissions to the devices in /proc/bus/usb, you'll need to
edit some rules in /etc/udev/rules.d.

Under gutsy, edit /etc/udev/rules.d/40-permissions.rules to say the following:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

HARDY HERON is Version 8.04 LTS
Under hardy, edit /etc/udev/rules.d/40-basic-permissions.rules to say the following:

```

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664", GROUP="vboxusers"
SUBSYSTEM=="usb_device",                MODE="0664", GROUP="vboxusers"

```

Then, restart the udev service:

```

sudo /etc/init.d/udev restart

```

Now, if you haven't done it already, make sure your user is part of the group vboxusers using the following command:

```

sudo adduser $USER vboxusers

```


Install the latest Version of VirtualBox with USB Support for Ubuntu 8.04 LTS.  

[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You should now have a menu selection for VirtualBox.  (Install the Guest Additions in the VirtualBox via the menu selection.)

VirtualBox will open in a Window.  After the initial install, you won't have the Virtual Disk Image (VDI).
You will have to create it and size it accordingly.  I assigned about 800 Meg of RAM to XP and 10 Gig to the
Virtual Disk Image.  After you have a VDI for Win XP created, insert the Win XP CDR in your DVD Drive,
and Install Win XP by clicking START.  After the Image is installed the VDI can be copied to other computers
and used by VirtualBox that is installed on any computer.

The first picture is of my Image that has the Allen Bradley RSLogics installed.

Go through the steps of setting up the VDI.
General, Hard Disks, CD/DVD ROM, Floppy, Audio, Network, Serial Ports, USB, and Shared Folders.

Note that Floppy is the Physical IDE Drive that is attached to the IDE Cable connected to the Motherboard, and will be assigned Drive A;.
A USB Floppy Drive will be Drive B:, and must have a FILTER turned on to ENABLE the Drive, which allows you to ENABLE the Drive in Win XP.

Click on START to run the VDI of Win XP.  Once Win XP is running, you can enable the USB Floppy by clicking on the USB selection,
or in the Devices Menu as shown on the next two Photos.  Note that ONLY WRITE ENABLED USB Devices can be mounted in Win XP.

The fourth photo is of my Ubuntu Shared Folder that Windows XP, running on VirtualBox can access.  Information about using a shared folder,
and how to enable it is on the VirtualBox site in the HOWTO: and FAQ: areas.

The last photo is of Windows Accessing the files in the shared folder.


The last things left to do are insert the CDR's for RSLinx, RSLogic 5, RSLogic 500, and RSLogic 5000, and  install the software in that order.
The best option is to download the files from Allen Bradley, and just install the Updated files assuming you have the proper Registration and Serial Numbers.

Once all Allen Bradley Software is installed just copy the Activations to C: via the Menu selection in the RSLogics Menu.  Note: EVRSI.SYS file permissions are -r-x------

Configure RSLinx for the Ethernet IP addresses, and Browse to see if RSLinx is working. 

Next set up the proper Proxy Server with Ubuntu 8.04, with the information from the IT department.

Now try to access the Internet and try out the RSLogics Software, to verify that everything is working properly.


lkraemer

---

