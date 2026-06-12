---
title: "unable to USB boot Ubuntu server 64bits on raspberry pi 4 2gb"
date: 2020-07-01
forum: Server Platforms
---

### Post by amen8 on 2020-07-01
following the latest official bootloader update by the raspberry pi team, i was able to usb boot using raspbian os, but not Ubuntu.
this is enough evidence that the firmware is fine and the machine has usb booting capability.
my full hardware specs:
-raspberry pi 4 2gb
-SanDisk Ultra 64gb 10 MicroSD XC-I
-kingstone MicroSD reader
(yes by usb boot I mean SD inserted in an SD reader then inserted in the usb port, this is just to completely eliminate any uncompatibility excuses for SSDs or Adapters)
now that we cleared up all the basics, here are the steps taken (per the official ubuntu wiki for arm processors, link [here]("https://wiki.ubuntu.com/ARM/RaspberryPi"))
1-created the ubuntu image on SD using raspberry imager, inserted to SD recepticle on the machine, powered on and signed in using SSH, then rebooted
2-executed: sudo apt update -y && sudo apt upgrade -y
3-unplugged the SD then inserted it to another machine to edit the config.txt file located in the boot partition (per the wiki page above):
changed the kernel line, [COLOR=#333333][FONT=&quot]added the initramfs line, and finally comment out (#) the device_tree_address
[/FONT][/COLOR]```

[COLOR=#333333]kernel=vmlinuz
[/COLOR][COLOR=#333333]initramfs initrd.img followkernel
[/COLOR][COLOR=#333333]#device_tree_address=0x03000000
[/COLOR][COLOR=#333333]
```
as a result my raspberry pi doesnt want to boot ubuntu anymore, not when the SD is inserted directly, nor when I use the SD reader and put it in the USB port.[/COLOR]

---

