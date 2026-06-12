---
title: "Installing Windows 8 / 10 on VirtualBox"
date: 2015-10-18
forum: Virtualisation
---

### Post by PopsTheSailor on 2015-10-18
I bought a new computer (Lenovo C355) and it came with Windows 8 and upgraded to Windows 10. I'm about to wipe it out and install Ubuntu Mate 15.04 on it. I then want to install VirtualBox and ultimately put the Win 8/10 system restore onto VirtualBox. I understand that starting with Windows 8, the windows product key is in the BIOS. Have people successfully setup a computer like this (base Ubuntu --> VirtualBox --> Windows 8 or 10 using a system recovery disk)?

Any tips, suggestions, tricks, etc. would be greatly appreciated.

---

### Post by TheFu on 2015-10-18
Support for 15.04 ends in January consider installing 14.04 which is supported until 2019.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) will help you make plans.

I've **never** used UEFI for any virtual machine and doubt the restore from a physical system backup will work without huge levels of effort. It may not be possible. I would plan on a fresh windows install and if the license you have is tied to the BIOS, expect difficulties with that too. I think there is a thread about that here somewhere, but I don't think they were using virtualbox.

---

