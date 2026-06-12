---
title: "Install Ubuntu to USB thumbdrive with encryption"
date: 2008-06-23
forum: Security
---

### Post by daedelus82 on 2008-06-23
Hi guys, has anybody had success at installing Ubuntu to a USB drive using full disk encryption?

Obviously I am using the 'alternate' installer. Tried with both 7.10 and 8.04.

I'm able to install to the internal HDD using encryption no problem at all, and I'm also able to install to USB thumbdrive *without* encryption. However when I combine the two (USB + encryption) I cannot get it to boot...

I tried editing /boot/grub/menu.lst and changing all references of (hd2,0) to (hd0,0), as when booting from USB it becomes hd0... This normally allows you to boot from USB, however when using encryption it doesn't work. The ubuntu logo appears however I do not get prompted for dm-crypt password.

Any help would be appreciated. Thanks

---

### Post by mrsteveman1 on 2008-06-23
The last time i tried this, either the kernel or the initrd didn't do it right, because it tried to load the cryptsetup scripts before the USB block device had even appeared to the kernel, so it sat there.

So unless this has been fixed the developers should look into pushing cryptsetup back further since it appears it loads to soon. I tested this on a number of different machines and got the same result.

---

### Post by daedelus82 on 2008-06-23
That could explain it. Thanks.

If the dev's could look into this, or if anyone has a workaround, thanks.

---

### Post by jeremybar on 2008-10-11
I am hitting the same issue with 8.04.1 i386.  I enabled logging (removed silent and splash from boot command line in grub) and the failure isn't obvious as the kernel stops booting with no error message after it displays the detection of the USB drive.  It seems to be a difficult one to diagnose ...

---

### Post by RUPARADOX on 2008-10-11
pendrivelinux.com - the answer :)

---

### Post by jeremybar on 2008-10-12
I managed to get the system to boot with encrypted USB by booting with quiet and splash removed from the kernel command line and waiting for the initrd script to timeout.  Then when dropped into a shell, you can run the cryptsetup command and exit the shell.  From this point, the system boots fine.

The command is:
cryptsetup luksOpen /dev/<whatever_your_USB_disk> usb_scrypt
Then exit the shell

Other information can be found here:
[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/195464](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/195464)

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/164044](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/164044)

Apparently, this issue is fixed in Intrepid.

Jeremy

---

