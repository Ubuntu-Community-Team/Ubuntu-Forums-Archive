---
title: "VBox Virtual Optical Drive Not Working Correctly (Ubuntu as Guest)"
date: 2012-09-29
forum: Virtualisation
---

### Post by p0wder2 on 2012-09-29
[SOLVED]  See reply below for details


Hi.  I've run into an issue which I cannot find an answer to after doing many searches.  There are plenty of threads on it, but none address the underlying problem:

In order to get Ubuntu to "see" anything in the "drive", I have to already have an ISO mounted when booting the system.  And if I want to change ISOs, I have to force an unmount in order to mount the new ISO and then reboot the system.  I am certain it has something to do with whatever causes the following error (which I get anytime I try to mount/unmount an ISO with the guest running):

Note, this is a VBox error NOT Ubuntu...


"Unable to unmount the CD/DVD image [path to ISO] from the machine [VBox VM].  Would you like to force unmounting of this medium?

Could not unmount the currently mounted media/drive (VERR_PDM_MEDIA_LOCKED)"


...If mounting instead of unmounting, it's basically the same error.  I thought "MEDIA_LOCKED" might mean I needed to eject from guest OS first, but that solves nothing.  Can anybody please help in correcting this issue???  Thanks.

---

### Post by p0wder2 on 2012-09-29
Quick answer:

Ensure your optical drive(s) are located on an IDE Controller!
(Settings, Storage on VirtualBox with VM powered off)
Also, still use eject in the guest OS as opposed to unmounting through VBox menu


Longer answer:

VirtualBox has it's own limited BIOS which doesn't support **booting** from SATA.  This is fine because the first four ports run in IDE compatibility mode until the guest OS is loaded in order to support booting from drives located on the SATA controller.

Until now, I've only run Windows VMs, so having everything on a SATA controller hasn't been a problem as long as I knew which ports function as PM, PS, SM, SS when installing windows from ISO.  However, this doesn't seem to work right in linux.  I have no idea why.  I even tried throwing the optical drive on a couple ports above 3 and no go.  But, putting it on an IDE controller worked fine.  Maybe someone else here knows why :)

---

