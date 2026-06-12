---
title: "Security Boot Fail"
date: 2016-12-01
forum: Ubuntu/Debian BASED
---

### Post by aescwyn on 2016-12-01
I tried to dual boot Windows 10(UEFI) and Ubunt 16.04.1 LTS. While installing I chose "Install Ubuntu alongside Windows Boot Manager" and was forced to restart after installation without managing to install efibootmgr. After restarting I was greeted by Windows 10 and grub didn't show. I typed the following command in Windows CMD:
[SIZE=3]
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[/SIZE] 
without disabling Secure Boot(dumb). I restart my laptop and grub showed and boot a few times to Ubuntu just to make sure I can really access Ubuntu & grub and then boot to Windows 10. After booting to windows I restart my pc but I got; "Security Boot Fail" *<snip>link removed</snip>*. I can't disable Secure Boot, I tried switching from UEFI to Legacy, but to no avail. Then somehow I got to access to boot manager (I don't know how) and manages to boot into Windows. Now I don't know what I should do, I'm scared to try something without consulting experts.

---

