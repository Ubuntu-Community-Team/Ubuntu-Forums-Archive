---
title: "Xen pciback troubles"
date: 2013-05-03
forum: Virtualisation
---

### Post by Jickler on 2013-05-03
Hello all,

I'm having a sporadic problem with Xen's PCI passthrough, but since I'm pretty confident that the problem lies within Ubuntu's boot sequence (that is my lack of understanding of the boot sequence) I thought it would be more appropriate to post here. In order to passthrough a device it has to be assigned to the pciback module instead of the device's actual driver during boot-up. This is accomplished by a grub parameter that specifies which PCI devices are to be bound to pciback. However, for this to happen correctly during boot-up the pciback module has to be loaded before the driver's real module (in this case radeon) because if radeon is assigned to the device obviously pciback can't be assigned as well. Here's the Xen wiki documentation on this: [http://wiki.xen.org/wiki/Xen_PCI_Passthrough#Static_assignment_for_xen-pciback_module](http://wiki.xen.org/wiki/Xen_PCI_Passthrough#Static_assignment_for_xen-pciback_module) . 

I've gotten this working without problems before, but since I started working on this 13.04 dom0 it's been extremely weird. I'm passing through two video cards and their respective audio devices, and pciback is assigned to all four devices maybe one out of five boots, pciback is assigned to the audio devices only one out of five boots and the other three times all four devices will load with radeon/snd_hda_intel. 

This is what I've done and why I think it should work: 
1) I added the xen-pciback module to /etc/modules, and even when the modules are incorrectly assigned lsmod still shows xen_pciback loaded. 
2) I created a file in /etc/modprobe.d called radeon.conf which contains the following:
```
install radeon /sbin/modprobe pciback ; /sbin/modprobe --first-time --ignore-install radeon
install snd_hda_intel /sbin/modprobe pciback ; /sbin/modprobe --first-time --ignore-install snd_hda_intel
options xen-pciback hide=(0000:04:00.0)(0000:04:00.1)(0000:05:00.0)(0000:05:00.1)
```

This is supposed to make the computer load the pciback module before the radeon and snd_hda_intel module (which clearly isn't working).

3) I added the xen-pciback.hide=(04:00.0)(04:00.1)(05:00.0)(05:00.1) parameter to grub, and I've even checked the boot line in the grub menu to make sure I'm booting what I think I'm booting. 
4) I've ran update-initramfs -u a billion and a half times.

When I look at dmesg I see radeon first being mentioned at: 
```
[   15.061096] [drm] radeon defaulting to kernel modesetting.
```
and pciback at:
```
[   16.952380] xen-pciback: backend is vpci
```
And 15 is less than 16, so I presume this means radeon is still being loaded first. How can I make this not happen? Thanks for any help that comes my way :)

---

### Post by heiko_s on 2013-05-07
Regarding your steps, you either load pciback as module via /etc/modules, or you put it on the initramfs and have it load via grub command. Someone posted a little how-to on preparing the initramfs: [Howto configure pciback module to load before most hardware modules (drivers)]("http://forums.linuxmint.com/viewtopic.php?f=42&t=112013&start=120#p711782"). You use either /etc/modules, or the grub command such as GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT="xen-pciback.hide=(02:00.0)(02:00.1)". 

There is also a way to blacklist the radeon module using a grub command. Edit /etc/default/grub and change/add as follows: GRUB_CMDLINE_LINUX_DEFAULT="radeon.blacklist=1". Not sure this is as effective.

After modifying the config files (grub, etc.), make sure you run:
    sudo update-initramfs -u -k all
    sudo update-grub

Good luck!

---

