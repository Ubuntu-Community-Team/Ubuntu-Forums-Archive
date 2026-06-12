---
title: "Trying to create a W10 boot USB."
date: 2017-04-20
forum: Windows
---

### Post by ianberg on 2017-04-20
I get as far as the Windows logo but get an error saying 0xc00000e. Saying to use recovery media to repair the system (though W10 has never been installed on this kit.)

I've checked several other answers and they don't help.

I've done the following.

    Create an msdos partition table on the device.
    Create a primary partition with type ntfs (tried with fat32 also).
    Set partition to bootable.
    Copy the contents of the iso to the drive. I did this using 'mount -o loop img.iso /mnt/temp/'. Then just used the file manager to copy the files across.
    run 'sudo ms-sys -7 /dev/sdb' from Terminal.

I am trying to use the USB stick on quite new hardware. It doesn't have an option for legacy boot. It has an option for secure boot. I've enabled it with factory default keys. I don't know if anything else is required. I also tried it disabled.

Please help. I only need W10 to upgrade my firmware. I hate it already and it's not even installed.

---

### Post by oldfred on 2017-04-20
Are you sure you need Windows 10 to update firmware?
Most have several ways. From Windows is one.
But usually you can use a FAT32 formatted flash drive. And either just have the extracted update file or make it a DOS bootable flash drive with update file.
Often download of firmware includes all options.

You cannot run Windows from flash drive. Just the installer. So I do not think Windows installer will let you run updates to firmware.

---

### Post by Perfect Storm on 2017-04-20
Moved to Windows forum.

---

### Post by johndough2 on 2017-04-25
Hi

I download the windows 10 iso and use CDburnerXP to create a DVD.  If you have the iso then a similar thing is available in most flavours.

---

