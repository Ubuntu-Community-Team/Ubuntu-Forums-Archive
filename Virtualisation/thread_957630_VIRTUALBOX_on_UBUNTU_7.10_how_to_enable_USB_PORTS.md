---
title: "VIRTUALBOX on UBUNTU 7.10 how to enable USB PORTS"
date: 2008-10-24
forum: Virtualisation
---

### Post by efsandino on 2008-10-24
Hi i want to enable USB PORTS in a Virtual Machine running WinXP on a VirtualBOX installation over my UBUNTU 7.10

¿Can anyone help me how to?

---

### Post by TenPlus1 on 2008-10-24
This is the text file I refer to when I need help: 


Once VirtualBox is installed, run this command to add vb into the user privelages:

sudo usermod -G vboxusers -a <username>


Check USB Support:

add the group:
sudo groupadd vboxusers


add usb support:
sudo groupadd usbusers
sudo gpasswd -a <yourusername> usbusers


gksu gedit /etc/udev/rules.d/40-permissions.rules


USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute 

/etc/init.d/mountdevsubfs.sh start



USB devices, add lines to end of file:

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"


sudo gedit /etc/fstab

add this line after other volumes:
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0


When running Windows or whatever Os, use the VirtualBox screen menu and install guest additions so you can access seamless mode...

This will let you share files between Ubuntu and XP (or whatever), use Net use x: \\vboxsvr\<user> to map drive letter to shared files.

If you have just installed a new kernel then you may have to run the following to get Virtualbox working again:

sudo  /etc/init.d/vboxdrv setup

-- alternative usb support for ubuntu 8.04 gutsy --

gksu gedit /etc/init.d/mountdevsubfs.sh

Change section so this is uncommented:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Last step: Reboot. USB devices should now be recognised under VirtualBox.

---

