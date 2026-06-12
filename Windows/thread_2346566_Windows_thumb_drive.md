---
title: "Windows thumb drive"
date: 2016-12-16
forum: Windows
---

### Post by pete1977x on 2016-12-16
In Ubu how can I copy a Windows 8 iso to a thumb drive to Use Windows from the thumb drive only.....like when you load ubuntu from a thumb drive and select try ubuntu instead of install..

---

### Post by howefield on 2016-12-16
Thread moved to the "*Windows*" forum.

---

### Post by sudodus on 2016-12-16
You can use ***mkusb-nox*** which is a command line tool, or the brand new tool ***guidus***, which does the same thing but with a graphical user interface. See the following links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Making a USB drive to install Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

or with the GUI

[mkusb/gui](https://help.ubuntu.com/community/mkusb/gui)

[dus - a revamped interface of mkusb and mkusb-nox](https://help.ubuntu.com/community/mkusb/gui#dus_-_a_revamped_interface_of_mkusb_and_mkusb-nox)

***Edit:*** You need no pre-formatting, mkusb-nox and guidus do it automatically.

---

### Post by C.S.Cameron on 2016-12-16
I think the op wants to "Try" Windows, not "Install" it.

I have used mkusb to build a Persistent 128GB USB3 Ubuntu 16.04 pendrive.
Installed VirtualBox on it and installed Windows 10 in VBox.
Have been using it for a couple of months now, mostly for Ubuntu but occasionally Windows.

There are programs out there like WintoUSB, These are installed from Windows not Ubuntu. 
Some are quite expensive and do the same job as mkusb-nox, making a Windows installer, not an actual install of windows.

---

### Post by sudodus on 2016-12-17
Thinking about it and rereading the first post, I think you are right, *C.S.Cameron*.

Anyway, *pete1977x*, you can tell us, so that we help you solve the correct problem.

---

### Post by yancek on 2016-12-17
The only thing I've seen which might work is explained at the link below, 'Windows to Go'.  It's a pretty convoluted process and I've never used it so I have no idea if it works and if so, how well.

[http://www.makeuseof.com/tag/create-portable-windows-go-usb-drive/](http://www.makeuseof.com/tag/create-portable-windows-go-usb-drive/)

---

### Post by pete1977x on 2016-12-19
windows to go sounds right.... but I doubt it works somehow.

---

### Post by sudodus on 2016-12-19
You cannot use the standard installer to do it. I have also read about methods to make Windows to boot from USB, but I have never used it, except the very basic pre-installation environment BartPE (based on Windows XP). This was long ago.

I have used and am using a work-around: I have Ubuntu in an external SSD, and Windows in a virtual machine in VirtualBox. This way it is possible to install Windows (inside VirtualBox) directly by connecting the iso file 'as a DVD disk'. And it is a portable system because Ubuntu is portable. Windows sees the same machine all the time, the virtual machine.

---

### Post by C.S.Cameron on 2016-12-19
The method on this page worked for Windows XP (SP1):  [http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf](http://tdoui.webs.com/Install%20And%20Run%20Windwos%20XP%20From%20USB.pdf)
I used it to power an entertainment center, (at the time Ubuntu did not support S-Video),
It was very slow, perhaps would be better on USB3.
Installing this was the most complicated thing I ever did on a computer.
The modified files eventually became available on PB.
There may be modern equivalents.
Sorry for the trip down memory lane.

---

