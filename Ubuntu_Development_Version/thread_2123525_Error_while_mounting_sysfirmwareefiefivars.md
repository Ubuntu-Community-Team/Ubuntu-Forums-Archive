---
title: "Error while mounting /sys/firmware/efi/efivars"
date: 2013-03-08
forum: Ubuntu Development Version
---

### Post by Yahoé on 2013-03-08
When booting from the latest USB Live, Raring amd64 on EFI (13-03-08), I get "an error occured while mounting /sys/firmware/efi/efivars".

If I ignore this message, the system reaches Unity, I'm able to proceed with an EFI install which completes without any errors, but upon rebooting the machine, it hangs on boot.

Any idea why I get  this error from the USB Live?

---

### Post by Yahoé on 2013-03-08
Investigating a bit further the installed EFI system also hangs with mountall reporting "an error occurred while mounting /sys/firmware/efi/firmware/efivars [1008] terminated with status 32.

I have two different systems experiencing the same problem (both Asus EFI Bioses, different models) with the latest 3.8.0-11-generic #20 kernel.

Assitance would be appreciated

---

### Post by Cobuntu on 2013-03-08
I have the same problem on my Fujitsu T902 running freshly updated 13.04. I used boot-repair two times when the first time left me unbootable, but then it also showed "an error occured while mounting /sys/firmware/efi/efivars". I then just pressed S to skip and it continues to the Unity log-in screen and everything works

---

### Post by Yahoé on 2013-03-09
Bump! I can't believe we are only two experiencing this when I have to machines affected.

Could anyone give me some pointers on what's happening and how to fix this?

---

### Post by oldfred on 2013-03-09
Not sure if this may be the issue or not.
But UEFIs have a shell that you can use to work with UEFI. It is like the command line in grub or Ubuntu. 
But not all UEFI include the shell, so the tools to extract the data are not there.

Do you have this entry and does it get you to a shell?
 EFI/boot/bootx64.efi.efi" ---> Brings up 'EFI shell environment' with command prompt.

 [https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell](https://help.ubuntu.com/community/UEFIBooting#UEFI_Shell)

 
 Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
UEFI generic shim - Secure Boot bootloader
[http://mjg59.dreamwidth.org/20303.html](http://mjg59.dreamwidth.org/20303.html)

---

### Post by Cobuntu on 2013-03-10
Thanx for your reply, unfortunately I do not understand how to get to EFI/boot/bootx64.efi.efi

After finding this, I guess it is a kernel bug in current 13.04 kernel, I did not experience this with 3.8.0.9 but after updating to 3.8.0.11: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1146868)
I do have /sys/firmware/efi/efivars and there are no files in it. Comment #8 seems to be the solution but I have no idea how to do this.

Updated to 3.8.0-12-generic, problem is gone. In /sys/firmware/efi/efivars I now have 93 files, before there was none.

---

