---
title: "Vmware cannot access usb devices"
date: 2012-01-04
forum: Virtualisation
---

### Post by azenz on 2012-01-04
Since upgrading to Oneric, I can apparently forget about getting USB devices recognized in Vmware player (running 4.0.1 with Windows XP guest).
 
The problem is that newer kernels no longer support CONFIG_USB_DEVICES, meaning that no /proc/bus/usb folder exists.
 
Moreover, this folder cannot be created or activated with /etc/fstab entries such as usbfs /proc/bus/usb usbfs auto 0 0, because kernel support for usbfs is no longer there. Apparently, usbfs is DEPRECATED and should NO LONGER be used! Instead, hal udev is to be used.
 
Are there workarounds? 
Will Ubuntu/Kubuntu users have to forsake Vmware completely?!
Others must have the same problem?!
Help and comments much appreciated, thanks!

---

### Post by fjgaude on 2012-01-08
Just noticed your post... I've had no issues with USB devices with 11.04, 11.10, and 12.04. I can't say why this is so but it is. VMware Player 4.0.1 simply works with all except 12.04, which requires a patch, at least until the Beta of it, i.e., 12.04, comes out.

---

### Post by dcstar on 2012-01-11
> **azenz said:**
> Since upgrading to Oneric, I can apparently forget about getting USB devices recognized in Vmware player (running 4.0.1 with Windows XP guest).
 
The problem is that newer kernels no longer support CONFIG_USB_DEVICES, meaning that no /proc/bus/usb folder exists.
 
Moreover, this folder cannot be created or activated with /etc/fstab entries such as usbfs /proc/bus/usb usbfs auto 0 0, because kernel support for usbfs is no longer there. Apparently, usbfs is DEPRECATED and should NO LONGER be used! Instead, hal udev is to be used.
 
Are there workarounds? 
Will Ubuntu/Kubuntu users have to forsake Vmware completely?!
Others must have the same problem?!
Help and comments much appreciated, thanks!

My 10.04 host does not have a /proc/bus/usb folder and VMware Player 4.01 and its guests all have perfect USB functionality.

Remove any of that old USBFS rubbish from the /etc/fstab file, it no longer applies.

---

