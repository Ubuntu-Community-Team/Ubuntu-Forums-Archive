---
title: "USB devices not seen in Virtual Box 4.0.8r71778"
date: 2011-05-19
forum: Virtualisation
---

### Post by Robbyx on 2011-05-19
natty ubuntu 11.04 hosting winxp pro. 

I have a problem seeing any usb devices from within VB. I posted a version of this in the forum at  VB's web site but no one is replying. 

Mine is a new installation of VB and WinXp pro.

The Oracle VM VB Extension pack is installed. It is ticked in pale green as active. It is the same version as VB above.

My ubuntu login name is in the vboxusers group.

The permissions in /etc/init.d/vboxdrv are correct at 750.

# Create the /dev/vboxusb directory if the host supports that method
# of USB access. The USB code checks for the existance of that path.
if grep -q usb_device /proc/devices; then
mkdir -p -m 0750 /dev/vboxusb 2>/dev/null
chown root:vboxusers /dev/vboxusb 2>/dev/null
fi
succ_msg

I have installed WinXp pro. It loads. No printers or other usb devices are showing in VB's devices -usb or in windows printers and faxes. It is not greyout out. It just shows nothing in the way of usb connections.

I would like some help to get the usb devices to work as I do not know what to add or alter.

Robin

---

### Post by b0b138 on 2011-05-19
You need to add the device to the machine before you start it.

In the settings goto the usb section and on the right you will be able to add usb devices to the machine.  They call them device filters.

---

### Post by Robbyx on 2011-05-19
> **b0b138 said:**
> You need to add the device to the machine before you start it.

In the settings goto the usb section and on the right you will be able to add usb devices to the machine.  They call them device filters.

I tried to follow your suggestion. I clicked on the settings and immediately had the following message:

[I]Failed to access the USB subsystem.
VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. Please see the user manual for a more detailed explanation.

Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {35b004f4-7806-4009-bfa8-d1308adba7e5}
Callee: 
IMachine {662c175e-a69d-40b8-a77a-1d719d0ab062}

[/I]

I checked and my user is part of the vboxusers group, so I do not know how to proceed.

Robin

---

### Post by b0b138 on 2011-05-19
You say its a new install of VB?

You have to logout/login or reboot for group permissions to take effect.

---

### Post by noidian on 2011-05-19
you need guest additions for USB enabled connections so ensure you have that installed as well. i presuem it was not installed or not installed correctly. Then use the GUI to add the devices.

---

### Post by Robbyx on 2011-05-19
> **b0b138 said:**
> You say its a new install of VB?

You have to logout/login or reboot for group permissions to take effect.

That was it. I had not realised that I had not rebooted since the installation! Thanks

Robin

---

