---
title: "after booting ubuntu , windows not bootable, boot-repair tool attempted"
date: 2018-06-30
forum: Windows
---

### Post by ravicm on 2018-06-30
[FONT=Roboto][FONT=sans-serif]I wanted to try ubuntu. So I created a bootable disk. In bios, changed UEFI to legacy, set boot priority. Booted ubuntu, tried it. Shut down the computer. Then I started, cannot start into windows. I see "no bootable device found. "


I have tried using boot-repair 4 times. I have Pastebin notes below. Can you please help?


I am stuck here, cannot get into windows. I am blocked on work. Can someone kindly help?. 


[http://paste.ubuntu.com/p/wCTHN3QsCz/](http://paste.ubuntu.com/p/wCTHN3QsCz/)
[http://paste.ubuntu.com/p/TsWr82Hs4V/](http://paste.ubuntu.com/p/TsWr82Hs4V/)
[http://paste.ubuntu.com/p/ddZGQdfYXH/](http://paste.ubuntu.com/p/ddZGQdfYXH/)
[http://paste.ubuntu.com/p/DsbTCZdnGN/](http://paste.ubuntu.com/p/DsbTCZdnGN/)



Thanks,
rc

[/FONT]



[/FONT]

---

### Post by ubfan1 on 2018-06-30
Did you change the BIOS/UEFI settings back to UEFI?  You really should install Ubuntu in the same mode as Windows to avoid having to switch modes.

---

### Post by oldfred on 2018-06-30
Windows also was left in hibernated state. So you have to boot from UEFI in UEFI boot mode and perhaps press f8 to get into Windows repair console. Or you need to use your Windows repair disk to fix Windows. 

You did backup & make Windows repair/recovery disk?

Moved to Windows sub-forum as no Ubuntu.

Boot-Repair is mostly for Linux repairs. It can only do very minor repairs to Windows systems & you need Windows tools to repair Widnows.

---

