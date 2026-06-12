---
title: "Mount USB in virtualbox(not OSE)"
date: 2008-05-25
forum: Virtualisation
---

### Post by Raccoon1400 on 2008-05-25
I have several OSs running in virtual box, and want the winXP one to mount USB. I created the filters for the devices, but when I go to mount them in the bottom right corner of the guest OS window, they are greyed out. Why?

---

### Post by robertchahine on 2008-05-25
> **Raccoon1400 said:**
> I have several OSs running in virtual box, and want the winXP one to mount USB. I created the filters for the devices, but when I go to mount them in the bottom right corner of the guest OS window, they are greyed out. Why?
**did you try that?**

1-sudo gedit /etc/fstab
2-paste this line to the end of your fstab:
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
3-sudo gedit /etc/init.d/mountdevsubfs.sh 
4- change the (original:
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb)

after change

#Magic to make /proc/bus/usb work

mkdir -p /dev/bus/usb/.usbfs
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

5-Find your vboxusers number
6-sudo gedit /etc/fstab
7-none /proc/bus/usb usbfs devgid= enter vboxusers number HERE,devmode=664 0 0
				   ---------------------------
8-sudo chown -R root:vboxusers /proc/bus/usb

9-reboot
10-open virtualbox and go to settings->general
11-enable IO APIC
12-settings->usb
enable USB, and add the USB devices to your VirtualBox with the green USB icon.(Deivces must be plugged in for this to work)

---

### Post by caver1 on 2008-05-26
Int the Virtualbox window highlight the machine you want USB with. then click settings. in the new window scroll down to USB and click on it.
Then on the right side check the boxes to enable USB. The USB ECHI is for USB 2 if you need it. then under USB filters Add the USB devices you want to use in that machine. Don't add mouse or keyboard. Be warned that the host and the guest cannot access the USB device at the same time.
Now the USB choices on the bottom right should work.
caver1

---

