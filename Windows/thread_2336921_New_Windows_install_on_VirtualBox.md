---
title: "New Windows install on VirtualBox"
date: 2016-09-12
forum: Windows
---

### Post by aeronutt on 2016-09-12
I'm considering buying a consumer (authentic, new, etc) Windows 7 for a fresh install into VirtualBox on Ubuntu, and I'm not up to date on the latest Windows anti-pirating technology.

So, a few questions:
- Any known difficulties or show stoppers?
- Will it transfer to a new/fresh install of Ubuntu on the same hardware as originally installed?
- Will it transfer to new hardware (again, on VB/Ubuntu)?
- Any differences for Windows 10 (although I'm really trying to avoid W10).

Thanks!

---

### Post by TheFu on 2016-09-12
I have a retail Win7 install that has moved through 3 different physical systems running KVM (not virtualbox).  The last move was from 10.04 to 14.04 KVM and required a **sysprep** and a few extra MSFT validation complaints, but it has been working perfectly.  I could have just reinstalled it, but didn't want to lose the WMC recording history.

Don't get an OEM install. Stay with retain, assuming you can find one still.

The point of using a VM is that actual hardware is abstracted from the OS.  However, all VMs do patch their apparent motherboard and BIOSes over time, which appear like new hardware to Windows.

Cannot talk at all about Win8-Win10. Never touched those.  For the last year, I've been avoiding, removing, preventing selected MSFT patches to force Win10 update and spying updates from MSFT. It got to the point that I don't let the Win7 machine access the general internet and only manually patch it after reviewing each patch. Some of the patches that I've hidden before have come back. MSFT has become very NASTY.  Found 35G of unwanted patches automatically downloaded from them - filled C:. Need to send MSFT a bill for my data use. Nasty changes there.

---

### Post by aeronutt on 2016-09-12
Thanks, good info.
Yea, I've read enough about W10 to do everything I can to not use that. Hate to hear that updates have become so ugly.
Kudos to the Wine guys, I'd happily us that but nothing I need seems to run on Wine.
Heck, I might just buy a cheap Windows box and load the 1 or 2 programs on it. I'd probably only use it a few times a month, and could turn it off otherwise.

---

### Post by Bucky Ball on 2016-09-12
*Thread moved to **Windows**.*

Although you are intending to use Win as a virtual machine, this is not about that but explicitly a discussion about "the latest Windows anti-pirating technology," and miscellaneous Win questions.

---

