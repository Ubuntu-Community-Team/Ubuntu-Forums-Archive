---
title: "installing windows 7 on new (extra) ssd when there is already ssd with ubuntu"
date: 2013-09-13
forum: Ubuntu Development Version
---

### Post by muktupavels on 2013-09-13
Hi,

I am thinking about buying new sdd on which I want install windows 7. Currently I have one ssd on which I have ubuntu 13.10 + 2 hdd for data.

Can I attach ssd to pc and simply install windows 7 on it? Will I be able to boot in linux after that? Will ubuntu and windows 7 share one efi partition?

Ubuntu is installed in uefi mode or whatever it is called.

Thanks!

---

### Post by sudodus on 2013-09-13
Yes, it is clean and (fairly) easy to install the operating systems on different devices. After installing Windows, boot Ubuntu and update grub. It is a little more complicated with UEFI, so you might need [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") to fix it.

---

### Post by cariboo on 2013-09-13
I haven't used Windows for quite a while, but last time I installed it, it needed a 100MB partition at the start of the first hard drive.

---

### Post by oldfred on 2013-09-13
If Ubuntu is UEFI you will want Windows in UEFI boot mode. Windows 7 from DVD only installs in BIOS mode with MBR partitioning. You then would have to go into UEFI/BIOS and change boot mode each time you rebooted.

 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


       Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.

---

