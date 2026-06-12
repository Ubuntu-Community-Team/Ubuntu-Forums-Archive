---
title: "WIN Host - Ubuntu VHD"
date: 2015-06-25
forum: Virtualisation
---

### Post by pendulous on 2015-06-25
I'm looking to add and boot ubuntu from a VHD drive on a Windows native partitioned system. I seem to be having difficulties setting this up with EasyBcd. 

My current working setup is:
 
[PHP]There are a total of 3 entries listed in the bootloader.

Default: Not set
Timeout: None
Boot Drive: C:\

Entry #1
Name: Windows 8.1
BCD ID: {current}
Drive: C:\
Bootloader Path: \WINDOWS\system32\winload.exe

Entry #2
Name: Windows 10
BCD ID: {8ff4bca2-eba4-11f4-8299-485f39cff3ac}
Device: [C:]\ATI_VHD\2015_W10.vhd
Bootloader Path: \Windows\system32\winload.exe

Entry #3
Name: Windows 7
BCD ID: {64ffabf2-1234-11f5-9062-a2f47fd2fb6c}
Device: [C:]\ATI_VHD\Windows7.vhd
Bootloader Path: \Windows\system32\winload.exe[/PHP]

I attempted to add the Ubuntu VHD, but boots directly into Windows. I'm believe i need to install Grub, but unsure how this is done without destroying the Windows MBR.

---

