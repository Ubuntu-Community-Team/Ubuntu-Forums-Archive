---
title: "Win7 Installer Crashing VM"
date: 2015-12-05
forum: Virtualisation
---

### Post by thierrywall on 2015-12-05
I am trying to get VGA Passthrough going and my current hurdle is setting a VM to boot with UEFI.
I create a VM in virt-manager.
Select UEFI as the firmware. 
Continue through the wizard and create disk and select Win 7 iso.
The VM boots fine, boots from the CD.
"Windows is loading files..." finished and the splash screen appears.

And a second or two after the splash screen appears, the VM crashes and is turned off.
I know the .iso is fine, I was able to install windows with it without UEFI without issues.

I am baffled and unsure where to look, and any help would be appreciated.

---

### Post by dellboy56 on 2015-12-05
Wrong thread for a start and second of all this is Ubuntu not Windows if your looking for Windows 7 issues post it on seven forums thanks

---

### Post by thierrywall on 2015-12-05
How so?
QEMU-KVM is crashing when UEFI is used, on an Ubuntu host.
It does not crash when SeaBios is used instead.

This leads me to believe this is an issues with UEFI/OVMF, or how it's configured.

---

### Post by thierrywall on 2015-12-05
Windows 10 as the guest seems to work fine.

---

### Post by KillerKelvUK on 2015-12-06
Any error messages output to syslog or libvirt logs?

Post back the libvirt xml pls also.

---

