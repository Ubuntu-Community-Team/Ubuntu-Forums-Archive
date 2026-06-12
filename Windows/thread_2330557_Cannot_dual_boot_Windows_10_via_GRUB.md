---
title: "Cannot dual boot Windows 10 via GRUB"
date: 2016-07-12
forum: Windows
---

### Post by blahbla2 on 2016-07-12
Hey all,

Am new to Linux. I installed Ubuntu alongside my Windows 10 installation, but am not able to switch to Windows via GRUB. I tried using the Boot Repair tool, but it does not seem to fix the issue.

Here would be the link to my Boot Repair summary - [http://paste2.org/wYbY3x9M](http://paste2.org/wYbY3x9M)

Could you please help me with this?

Thanks

---

### Post by oldfred on 2016-07-12
Grub only boots working Windows.
Or you cannot have Windows fast start up on which is hibernation, nor can it need chkdsk.
Since Boot-Repair cannot read sda5, you may have fast start up on.

Grub also will not boot Windows when UEFI Secure Boot is on, Boot-Repair says you have it on. 
Something about the chain of security from grub to Windows does not yet work. 
If you want Secure Boot on, you have to boot from UEFI, or one time boot key, often f10 or f12, some f8 or f9 check your manual.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

---

