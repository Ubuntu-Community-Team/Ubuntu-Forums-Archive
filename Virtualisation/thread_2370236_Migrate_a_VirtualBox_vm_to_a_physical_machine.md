---
title: "Migrate a VirtualBox vm to a physical machine"
date: 2017-09-01
forum: Virtualisation
---

### Post by satimis on 2017-09-01
Hi all,

Host - Ubuntu 16.04
VM - Ubuntu 16.04 desktop
Oracle VirtualBox

Please advise the easy way to migrate a VM to a PC?

On googling I found many suggestions, following being an example;

Migrate from a virtual machine (VM) to a physical system
[https://askubuntu.com/questions/32499/migrate-from-a-virtual-machine-vm-to-a-physical-system](https://askubuntu.com/questions/32499/migrate-from-a-virtual-machine-vm-to-a-physical-system)

Thanks in advance.

Regards
satimis

---

### Post by TheFu on 2017-09-01
Backup the VM using normal backup tools.
Restore the VM to a physical computer using the same tools.

Perhaps run sudo grub-install ; sudo update-grub
Be happy.

Might want to remove the vbox guest additions before doing the backup or any other specific HW drivers that do not exist on the real hardware.

---

### Post by lammert-nijhof on 2017-09-01
I used the Disks Utility of the Virtual Machine to create a disk image of the sda drive. You will have to attach the drive temporarily to another VM (or you have to clone the VM), because you can't create an image involving an active OS. I used the Disks Utility of a life-ISO image to restore that disk image to the physical sda drive. Afterward you can use gparted to change the partition size and to create additional partitions, if needed. 

Before creating the disk-image, first make sure that your VM set-up is as equal to the HW machine as possible, especially go back to video without 3D support and look at IDE/SATA choices. You could remove all non-essential devices for network, sound, USB etc. If needed, you could also remove the guest additions, but that is command line job. I did not remove non essential devices and I did not remove the guest additions in my case. There are some good descriptions, how to 'remove guest additions', if you google for it.

If you want to restore the OS on another partition as sda1, it gets more complicated; You will have to create the disk image of the partition itself and restore that to e.g. sda3; After that you have to run grub-install and update-grub and you might have to adapt /etc/fstab and /boot/grub/grub.config manually. For the last one use 'find and replace' of gedit and replace 'hd0,msdos1' everywhere with in  my example 'hd0,msdos3'. For a dual boot with windows, it is easier to install Ubuntu first and to replace it with that partition image directly after the install, if you are really that fond on it :).

---

### Post by satimis on 2017-09-01
Hi all,

Thanks for your advice.

I use "Export Appliance ..." of "Oracle VM VirtualBox Manager" to export the VM as image.ova then use "Import Appliance ..." to import it back to "Oracle VM VirtualBox Manager" which has been done by me in the past without fail.

Now I'll copy the image.ova to a USB drive.  Unfortunately the image.ova can't boot PC.  

Whether use a LiveCD to boot the PC?
Then what will be the next steps?

Thanks

Following thread explains howto uninstall Guest Additions
How to uninstall Guest Additions in Ubuntu guest?
[https://forums.virtualbox.org/viewtopic.php?t=7839](https://forums.virtualbox.org/viewtopic.php?t=7839)

Regards
satimis

---

### Post by TheFu on 2017-09-01
Export from vbox isn't a "normal backup tool."

You should use something like rdiff-backup, dd, clonezilla, duplicity, dejadup, back-in-time .... you know ... normal backup tools.  Forget that it is a VM.

---

### Post by satimis on 2017-09-01
> **TheFu said:**
> Export from vbox isn't a "normal backup tool."

You should use something like rdiff-backup, dd, clonezilla, duplicity, dejadup, back-in-time .... you know ... normal backup tools.  Forget that it is a VM.
On VirtualBox the backup tool is clone.  To backup a VM is to clone a VM.

If to use Linux backup tool/command
on a VM folder:```

.Logs
ub1604dkpc1_00.vbox
ub1604dkpc1_00.vbox-prev
ub1604dkpc1_00.vdi

```
which of them shall I backup with Linux backup tool/command

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-09-01
> **satimis said:**
> On VirtualBox the backup tool is clone.  To backup a VM is to clone a VM.

If to use Linux backup tool/command
on a VM folder:```

.Logs
ub1604dkpc1_00.vbox
ub1604dkpc1_00.vbox-prev
ub1604dkpc1_00.vdi

```
which of them shall I backup w
err, no, TheFu is suggesting do a backup **from inside the VM** to a physical disk, i.e. boot your VM and back it up the same way you'd backup your bare-metal systems.

---

### Post by satimis on 2017-09-02
Hi all,

Following thread explains the steps migrating a VM to a physical PC;

Migrate from a virtual machine (VM) to a physical system
[https://askubuntu.com/questions/32499/migrate-from-a-virtual-machine-vm-to-a-physical-system](https://askubuntu.com/questions/32499/migrate-from-a-virtual-machine-vm-to-a-physical-system)

I'll come back after testing

Regards
satimis

---

### Post by TheFu on 2017-09-02
> **halogen2 said:**
> err, no, TheFu is suggesting do a backup **from inside the VM** to a physical disk, i.e. boot your VM and back it up the same way you'd backup your bare-metal systems.

Exactly.  Why do something complicated when you already use normal backup stuff for your systems.
Cloning a VM is not a backup. It is an image.  Those are VERY different things.

Backups are versioned, efficient with storage, automatic.  
Images are none of these things.  If you don't have 60 days of backup versions, then you don't have a backup for the system, IMHO.

A clone is not a backup.
A mirror is not a backup.

---

### Post by lammert-nijhof on 2017-09-03
Well I advised to use the disk utility to make an disk-image of you virtual disk and that is NOT the same as exporting a Virtual Machine. The latter is for re-use of the VM as VM in another computer. I have the feeling that it is wise to forget about this action and first get a better feeling about some of the basic concepts involved. What is:
- a vdi file or other VM disk files like e.g. vmdk.
- a disk image, a raw image or a compressed image
- a partition or disk back-up
- a partition image, a raw image or a compressed image and the difference with a disk image
- boot loaders, disk- and partition images
and if needed dual booting with windows and linux

---

