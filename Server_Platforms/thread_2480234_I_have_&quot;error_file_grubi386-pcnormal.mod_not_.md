---
title: "I have &quot;error: file /grub/i386-pc/normal.mod not found&quot; on ubuntu 22.04 server"
date: 2022-10-23
forum: Server Platforms
---

### Post by Tatiana_ on 2022-10-23
[COLOR=#232629][FONT=-apple-system]I've got error: file /grub/i386-pc/normal.mod not found on ubuntu 22.04 server.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I found this document and try but nothing worked for me: [https://www.linuxtechi.com/boot-ubuntu-22-04-rescue-emergency-mode/](https://www.linuxtechi.com/boot-ubuntu-22-04-rescue-emergency-mode/)[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I cannot get into rescue mode when I do all these steps. 
The boot line looks differently for me too. 
What am I missing? 
Or maybe there are some better ways to address this problem?[/FONT][/COLOR]

---

### Post by oldfred on 2022-10-23
Often from having installed grub in both BIOS & UEFI boot modes with last install's only version that works. But then trying to boot old version of grub.
Are you booting in correct boot mode? New systems are all UEFI, but some users have very old BIOS systems from Windows 7 era or have installed in old BIOS mode.

Needs gui, so you need desktop installer or can download Boot-Repair ISO which may not be quite as current as ppa.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

