---
title: "VirtualBox: Strange window on install of openSUSE 11.1"
date: 2009-01-16
forum: Virtualisation
---

### Post by johnaaronrose on 2009-01-16
Using Ubuntu Hardy kernel 2.6.4.23-generic and Guest 2.6 Linux OS. After adding iso image for openSUSE 11.1 and trying to install openSUSE to Guest, I got the standard openSuse DVD window and selected Installation. I then got unhelpful error window (attached) with title of Guru Meditation. It states that a critical error has occurred. VBox.png is attached and shows black screen. Uploading site software states that VBox.log is an Invalid file! Relevant section of VBox.log shows:
00:01:11.466 !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
00:01:26.480 Changing the VM state from 'RUNNING' to 'GURU_MEDIATION'.
00:08:32.484 Console::powerDown(): a request to power off the VM has been issued (mMachineState=6, InUninit=0)
00:08:32.493 Changing the VM state from 'GURU_MEDIATION' to 'OFF'.
00:08:32.493 Changing the VM state from 'OFF' to 'DESTROYING'.

Help please!

---

### Post by Dedoimedo on 2009-01-16
A few questions / suggestions:

Did you configure the virtual machine to use an ide or scsi hard disk device?

Try booting in safe graphic mode.

Try booting with acpi=off added to the GRUB entry. Do you know how to interactively edit GRUB?

Dedoimedo

---

### Post by johnaaronrose on 2009-01-16
I tried a downloaded openSuse 11.1 iso image & the resultant DVD. Both gave the same problem. However, I then tried a previously created openSuse 11.0 DVD and that worked OK!

Not sure about SCSI versus IDE. I didn't change the default. Ubuntu regards the actual hard disk as scsi.

Not sure what you mean about interactively amending grub. Do you mean amending /boot/grub/menu.lst on Host OS i.e. Ubuntu Hardy Desktop?

---

### Post by Dedoimedo on 2009-01-16
Nope. I meant pressing e to edit the menu, pressing e on relevant entry, adding a piece of code you want, pressing e to boot.
Dedoimedo

---

