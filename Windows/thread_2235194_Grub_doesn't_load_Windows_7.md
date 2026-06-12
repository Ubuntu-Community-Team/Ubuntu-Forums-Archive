---
title: "Grub doesn't load Windows 7"
date: 2014-07-19
forum: Windows
---

### Post by Guillermo_Martne on 2014-07-19
Hi there!

I've just installed first Windows 7 and then Ubuntu 14.01. After installing Ubuntu, I can't load Windows so I ran Boot-Repair from LiveCD. After doing so, grub seems to work, and there's no problem loading Ubuntu. However, when I try to load Windows 7, the following error message appears:

error: file `/boot/grub/x86_64-efi/ntfs.mod' not found.
error: failure reading sector 0xfc from `hd1'.
error: failure reading sector 0xe0 from `hd1'.
error: failure reading sector 0x0 from `hd1'.
error: failure reading sector 0xfc from `hd1'.
error: failure reading sector 0xe0 from `hd1'.
error: failure reading sector 0x0 from `hd1'.
error: no such device: E06ACC146ACBE4FE.
error: can't find command `parttool'.
error: invalid EFI file path

I've had a lot of problems trying to install windows and ubuntu with dual boot. My computer is an Asus X551C with Windows8 preinstaled. I deleted all partitions and installed windows and ubuntu.

Thanks in advance!

---

### Post by oldfred on 2014-07-19
Did you install Windows 7 in UEFI or BIOS. The DVD defaults to BIOS only, but you can copy to flash drive and do some updates to make it a UEFI installer?

And if you installed Windows in BIOS mode, you must be sure to install Ubuntu in BIOS mode.
UEFI & BIOS are not really compatible and once you start booting in one mode you cannot change. Or from grub menu you can only boot systems installed in same boot mode.

Best to see details, post link to new run of BootInfo report:[URL="https://help.ubuntu.com/community/Boot-Repair"]
https://help.ubuntu.com/community/Boot-Repair[/URL]

---

### Post by Guillermo_Martne on 2014-07-20
Thanks for your message oldfred! I finally got to solve it with boot repair assistant in WindowsCD (Don't know how I did it, though :-P )

---

