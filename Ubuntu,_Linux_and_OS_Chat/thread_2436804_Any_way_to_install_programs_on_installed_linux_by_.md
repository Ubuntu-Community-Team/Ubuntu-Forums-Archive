---
title: "Any way to install programs on installed linux by booting from bootable usb?"
date: 2020-02-13
forum: Ubuntu, Linux and OS Chat
---

### Post by shylyraging on 2020-02-13
Suppose I have flashed a linux iso on usb, and used that usb to install in on my laptop, is there a way to install some programs to my installed os (laptop) by booting from the usb (using the try ubuntu feature)?

---

### Post by TheFu on 2020-02-13
Yes.  Just install them.

The install is temporary for that session alone. If you reboot, then those packages would need to be reinstalled since an ISO is read-only media.  Most tools are tiny and install in 5 seconds.  OTOH, if you are trying to setup a flash based Java/Android development environment, best to just install onto a HDD or SSD. Wasting 45-90 minutes getting environments like those setup is a waste of time more than once a year.

---

### Post by crip720 on 2020-02-13
Imagine there is, but be a long way to go about it.  I know you can download a program to the USB and then copy it to the installed version and install it.  Like if you deleted network manager, before downloading another version.  Usually a lot faster and easier just to install.

---

### Post by yetimon_64 on 2020-02-13
> **shylyraging said:**
> Suppose I have flashed a linux iso on usb, and used that usb to install in on my laptop, is there a way to install some programs to my installed os (laptop) by booting from the usb (using the try ubuntu feature)?

You can do so by using chroot (change root). You would need to bind mount several system directories and files between the usb live image and the laptop installation and use the chroot program to change the root filesystem in use to that of the laptop installation. From there you can then update or install to the laptop installation while working from the live image.

**Edit:** Note "chroot" is a CLI (terminal) program only so you would need to be comfortable using the terminal. I just noted your join date and if you are new to linux as well this is NOT a recommended technique for new starters unless absolutely necessary and under careful instruction.

I used to script this for updating multiple linux installs from a parallel install (multi-booting of several Linux installations on the same drive), though any grub updates would cause a massive problem so I eventually stopped doing so. I have also used this technique from a live image to do repairs to installed systems. You probably could install new applications via this method though it is far simpler to boot into the laptop if you can and install from there.

You would need to research using chroots and bind mounting of directories and files. I haven't done this for about 3 or 4 years now and am out of touch with the method currently. Though be aware that certain system applications, like the grub bootloader, will not like you doing this if it involves them and you can mess up an installation very easily; a bit like "here be dragons" ;).

Unless you have a serious installation fault that needs repairing just boot into the laptop and install directly, doing so will save you a lot of grief if things go awry while trying this chroot technique.

Regards, yeti.

---

