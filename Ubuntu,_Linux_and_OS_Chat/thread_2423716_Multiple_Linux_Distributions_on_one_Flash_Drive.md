---
title: "Multiple Linux Distributions on one Flash Drive"
date: 2019-07-27
forum: Ubuntu, Linux and OS Chat
---

### Post by Shibblet on 2019-07-27
Is there a program out there that will allow me to make a bootable USB drive that can load multiple ISO files?

What I want to do is take a 32g USB drive, and be able to boot the installer of Ubuntu, Kubuntu, Xubuntu, Ubuntu MATE, and Ubuntu Budgie.

---

### Post by TheFu on 2019-07-27
Yes. There are multiple.  The last time I did this, probably 3+yrs ago, I used yumi, but there are others.  Yumi takes the ISO files and expands them onto the flash media in a specific way.  Most of these solutions will only boot specific distros, since some ISOs aren't built in a way to support a live environment.

There are some based on the qemu emulator that will let you run the ISOs directly on the same machine, concurrently.

In the end, I found it too much hassle to keep my 32G USB3 flash storage current. I suppose if I wanted to show it to a bunch of people and let each of them try it on their own machines, then having a flash drive could be handy.  In general, I only need a USB or SDHC storage to boot when a physical install needs a little extra care.  Most of the time, I'd much prefer using a virtual machine.

---

### Post by oldfred on 2019-07-27
You can also do it yourself by installing grub directly to flash drive and use grub2's loopmount to boot ISO. You need to make it UEFI or BIOS as then that would be how it installs.

       [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
examples
[URL="https://gist.github.com/Pysis868/27203177bdef15fbb70c"]https://gist.github.com/Pysis868/27203177bdef15fbb70c
      [/URL]
 How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive#Workstation_live_medium](https://wiki.archlinux.org/index.php/Multiboot_USB_drive#Workstation_live_medium) 
    
        How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images, manual grub install
[http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498) 
    
[URL="https://gist.github.com/Pysis868/27203177bdef15fbb70c"]
[/URL]

---

### Post by C.S.Cameron on 2019-07-28
The nice thing about, YUMI (BIOS), is that each OS can have "unlimited" persistence. YUMI (UEFI), is limited to 4GB casper-rw and 4GB home-rw persistence per OS.
MultiBootUSB is another nice multibooter that works BIOS or UEFI but is limited to 4GB + 4GB persistence per OS.
You can also create a GPT partition table on the USB, divide it into as many partitions as you have OS and do a Full install of an OS on each. 
You can also use UNetbootin to install multiple persistent OS to a multi partition USB drive.
I prefer using mkusb as the basis for Multi OS drive: [https://askubuntu.com/questions/1097919/install-grub-on-a-multi-partition-and-multiboot-usb-flash-drive/1098055#1098055](https://askubuntu.com/questions/1097919/install-grub-on-a-multi-partition-and-multiboot-usb-flash-drive/1098055#1098055)

---

