---
title: "Vbox Guest - win xp &amp; usb devices"
date: 2009-10-17
forum: Virtualisation
---

### Post by vandalous03 on 2009-10-17
Hello.i've setup vbox on my ubuntu host and i have windows xp vm as guest.
The question is,how can i attach usb storage devices to the guest machine?
I ask this cause when i plug my usb stick the host mounts it but the guest doesn't.

Im using ubuntu 9.10b/9.04 32bit

Thanx in advance!

---

### Post by noelvh on 2009-10-17
I have been using Vbox for some time and have a write up I have been using the write up is from 8.04 but I have still been using it, and it works. One thing to not is I do not use the Vbox from the repos. I get the .deb fro the sun website. It is a bit of a pain as you have to update it your self but it supports the features better. I hope this will help you.

Noel

> Step 2: Setup User groups & USB support
*Add yourself as a virtual box user
In a terminal type:
sudo adduser username vboxusers
You must replace userame with your user name!
Or you can do this with the GUI user manager.

*Add USB support to you fstab file
In a terminal type:
sudo gedit /etc/fstab
And paste this line to the end of your fstab
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0

*Enable USB
In a terminal type:
sudo gedit /etc/init.d/mountdevsubfs.sh
You need to look for this section:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
And delete all the # shown, it should look exactly like this.

#Magic to make /proc/bus/usb work

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

Find your vboxusers number
In a terminal type:
sudo gedit /etc/group

Look for this, the number following it is your vboxusers number
vboxusers:x:NUMBER

Next you have to add a line to your /etc/fstab to allow usb mounting
In a terminal type:
sudo gedit /etc/fstab

Add this line:
none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0

Allow access to /proc/bus/usb/
in a teminal type:
sudo chown -R root:vboxusers /proc/bus/usb

Once you Log out or reboot, you can start VirtualBox (Applications>System Tools>Innotek VirtualBox)

Vbox mount share folder in windows guest (VM machine).
net use x: \\vboxsvr\your share folder name
The your share folder name in a folder you create in the host machine, so enter that folder name in the net use command.

---

### Post by fcmugen on 2009-10-17
There is a simpler version, go to 
System >Administration>Users and Groups
Then Unlock it, click on your user name, properties
Should be a tab called Groups, scroll all the way to the buttom of that list and just click on vboxusers. Thats it

---

### Post by Perryg on 2009-10-18
You can add VirtualBox to your repo list (software sources) under third party. (it is described on the VBox site download page) and any new versions will be installed during a normal upgrade. If you have installed dkms then any update to the Linux image will also update the build files and recompile VBox. For peace of mine I usually leave it un-ticked until I want to actually install it and then select it when I want to install the new version.

Now USB in Windows using Ubuntu is actually easier than one thinks.  All I do is install VBox, Run the following line as SU:
usermod -aG vboxusers <your username> (replace <your username> with you login name) Then a reboot of the host system so everything is in place.
Next you need to make sure that the USB/USB2 has a checkmark in it, then install a filter.  Now when you start the Windows Guest this will disconnect the USB device from the host and install it in the guest.  
If you only want to use the USB device every once in a while you can leave off the filter and then in the guest you click on device tab and go to USB and select the device you want to use.

---

