---
title: "What is your favourite multi-iso boot tool?"
date: 2020-11-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Ice-Tea on 2020-11-01
Done it years ago with a Windows but never done it with Linux.

---

### Post by oldfred on 2020-11-01
Doing it myself for understanding and control.
I also now use grub2's loopmount to boot ISO on one hard drive to install to another.
Now that flash drives are larger, I typically do a full install and also copy ISO to drive.

ISO boot & link to examples
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://gist.github.com/Pysis868/27203177bdef15fbb70c](https://gist.github.com/Pysis868/27203177bdef15fbb70c)

[https://wiki.archlinux.org/index.php/Multiboot_USB_drive#GParted_Live](https://wiki.archlinux.org/index.php/Multiboot_USB_drive#GParted_Live)

Others:
Tools for booting ISO
[http://ubuntuforums.org/showthread.php?t=2289225](http://ubuntuforums.org/showthread.php?t=2289225)

---

### Post by VMC on 2020-11-01
Ventoy & [grub2-ISO-boot]("https://help.ubuntu.com/community/Grub2/ISOBoot/Examples")

---

### Post by TheFu on 2020-11-01
I like using **virt-manger**.  Point at any ISO file and tell it to boot. Runs inside a virtual machine, so all the weird hardware doesn't matter as KVM+QEMU provide extremely standard hardware for the ISO to see regardless of what the physical machine has.

---

### Post by Ice-Tea on 2020-11-02
Thanks all for the info and links , loopback and virt-manger looks interesting.

Lots of complaints online about Ventoy triggering virus scanner alerts and altering registry keys.

---

### Post by VMC on 2020-11-02
> **lucap2 said:**
> Thanks all for the info and links , loopback and virt-manger looks interesting.

Lots of complaints online about Ventoy triggering virus scanner alerts and altering registry keys.
I only see Ventoy issues on Windows. Usually they are false positives as this suggests:
[https://github.com/ventoy/Ventoy/issues/31](https://github.com/ventoy/Ventoy/issues/31)

---

### Post by Ice-Tea on 2020-11-03
Rather mixed views on big forums like reddit as some feel the negativity is political based due to the country of origin of the project yet others feel any Dev worth their salt would work with the virus Companies to prove that they are false positives.

I don't know what to make of it.

---

### Post by mastablasta on 2020-11-03
Yumi on windows.
Multiboot USB on Linux: [https://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](https://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

---

