---
title: "Dual-boot: Windows doesnt boot properly."
date: 2009-02-03
forum: Windows
---

### Post by ShakeyJake on 2009-02-03
Hi guys,

I have a small partition on my hard drive that I recently installed XP to. It all worked and I logged in etc etc. I wanted to configure the drivers so I shut the pc down and booted into Ubuntu to download the stuff I needed. 

Now whenever I try to start Windows I get the 'starting' screen (with the logo and the loading bar) but then just a black screen, nothing.

I think the problem is most likely with XP itself, seeing as grub recognizes everything and XP tries to start.

Any help much appreciated,
Jack

---

### Post by kestrel1 on 2009-02-03
Could be that XP has a problem with a system file. You could try to repair Windows from the recovery console.
You need to boot from the Windows CD & select to enter the recovery console, select your windows install & type ```
chkdsk -r
```
at the command prompt. Not tried this on a dual boot, so it may knacker Grub, not sure on that though. If it does it is easy eanough to re-instate Grub:
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by ShakeyJake on 2009-02-05
Ah-ha, perfect.

Thaanks kestrel, I have no idea how to use a Windows console.

Now, if only I could get sound working, but that's a different thread. . . . . .

---

