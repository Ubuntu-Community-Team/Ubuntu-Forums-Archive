---
title: "How to install Windows 7 from USB?"
date: 2017-10-14
forum: Windows
---

### Post by auran2 on 2017-10-14
Hello there,
After a long time attempting to run Wine on my laptop running Ubuntu 16.04 LTS with no success, I finally gave in and decided to reinstall Windows 7.
I might dual boot Ubuntu again in the future, however, for now I'll just switch back to Windows.
So, how can I burn a Windows 7 .iso file to USB and install it? And if I do such, will it uninstall Ubuntu automatically? If not how do I remove it?
Thanks in advance,
Auran
(NOTE: This is my third post on this, I edited out the information from the others due to typos and straight up mistakes with the title)

---

### Post by Bucky Ball on 2017-10-14
To delete Ubuntu, boot from the media you installed it with, launch Gparted and delete the Ubuntu partition and any other partitions on that drive. (Partitions need to be unmounted to delete so right-click/'Unmount'. If you want to wipe all partitions, unmount them all then 'Device> Create new partition table'.)

This will get rid of the partitions, but grub may still be around. Hopefully someone can help with the finer points of removing that.

As for Windows on a USB, you will have much better luck (and probably more quickly) searching for awhile and asking on a Windows forum rather than asking here, but you never know your luck. Good luck. ;)

---

### Post by sudodus on 2017-10-14
You can use mkusb to create a Windows install USB drive. See this link,

[mkusb - Windows USB install drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)

Install mkusb with the following commands (while running Ubuntu),

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

or from a compressed image file, if you have already wiped Ubuntu but can use some other computer, where you can extract and clone from the compressed image file to a USB pendrive. See this link

[mkusb - Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

[hr][/hr]
I think you can let the Windows installer overwrite the whole drive (which means that you need not remove Ubuntu before you start the Windows installer).

---

### Post by yancek on 2017-10-14
Another option to create a windows bootable flash drive from the iso is explained below.  

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by auran2 on 2017-10-16
Hello everyone, quick update regarding my situation on the question I asked that started this thread in the first place.
So... I gave it a bit more thought and... I decided I'll figure out another way to install Wine on my system, I might just reinstall Ubuntu or something.
Thanks for everyone's help, despite that

---

### Post by Bucky Ball on 2017-10-16
Ok. Please mark as solved and post a new thread for any new issues.

Good luck. ;)

---

