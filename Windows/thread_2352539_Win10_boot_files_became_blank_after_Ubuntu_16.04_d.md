---
title: "Win10 boot files became blank after Ubuntu 16.04 dual boot installation"
date: 2017-02-13
forum: Windows
---

### Post by ya-ke on 2017-02-13
[FONT=arial]Hello all, please help me!

I have a dell inspirion with pre-installed Windows 10, on which I've installed Ubuntu 16.04 as dualboot, according to this [guide]("http://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/"), I've disabled secure boot.

In order to get the Ubuntu installation to work I ran boot repair (The Ubuntu installation crashed every time before I ran boot repair, but before I ran it, windows booted normally)[/FONT]
[FONT=arial]
I've set it up so both Linux and WIndows boot from the same EFI partition (/dev/sda1/ which is mounted on /boot/efi), but the boot file for Win10 (which is called bootmgfw.efi) is somehow blank. [/FONT]
[FONT=arial]

Right now when I try to boot using the bootmgfw.efi file from grub, I get this:




/EndEntire


file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,c8800,96000,ec9d3a6356fca941,9d,10)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: premature end of file (hd0,gpt2)/EFI/Microsoft/Boot/bootmgfw.efi


Press any key to continue...


When I press any key, it just goes back to the grub menu and I can't start windows 10, but can start Ubuntu 16.04

I've looked around for this kind of problem, ended up finding [this page]("https://ubuntuforums.org/showthread.php?t=2184137"), which wasn't very helpful.


I also lerned that boot repair creates a backup folder for boot files, but in this backup folder i found:
 - one file (bkpbootx64.efi) that is weirdly also blank
 - another file (bootx64.efi) which if I run from grub, just takes me back to the normal grub menu.

Any of the dell SOS boot files didn;t prove to be useful also.


Any help would be very much appreciated,

ya-ke[/FONT]
[COLOR=#000000]
[/COLOR]

---

### Post by yancek on 2017-02-13
If you ran boot repair with the 'Create BootInfo Summary' option, you should have a link to post here with the output.  Without that, any suggestions made will be pure guess work.

---

