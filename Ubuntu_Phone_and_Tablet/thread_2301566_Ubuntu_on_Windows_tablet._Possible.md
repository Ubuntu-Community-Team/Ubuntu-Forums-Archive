---
title: "Ubuntu on Windows tablet. Possible?"
date: 2015-11-03
forum: Ubuntu Phone and Tablet
---

### Post by Genetix111 on 2015-11-03
Hello everyone. I'm new on this forum. I would like to kindly ask, if there is any way to install Ubuntu on a tablet with Windows OS.

**_Specs:_**
[SIZE=2]MultiPad Prestigio Visconte Quad[/SIZE][SIZE=2]
- Intel® Quad-Core 1.83 GHz
- 1 GB RAM
- Windows 10
[http://www.prestigio.com/catalogue/MultiPads/MultiPad_VISCONTE_QUAD](http://www.prestigio.com/catalogue/MultiPads/MultiPad_VISCONTE_QUAD)

If there is a way to install my favourite OS on this little friend of mine, can you post a link with how-to? I already tried it, no success yet.


[/SIZE]

---

### Post by Vladlenin5000 on 2015-11-03
Hi and welcome.

I don't see why not... What have you tried exactly?

---

### Post by Genetix111 on 2015-11-03
tried to install it from usb and directly from tablet (iso file)

---

### Post by Vladlenin5000 on 2015-11-03
You need to change the boot order in BIOS/UEFI and most likely you need a physical keyboard and mouse via external USB hub and microUSB to USB adapter, of course.
The USB needs to have the proper support for UEFI. If done in Windows I recommend Rufus with the option GTP/UEFI.

---

### Post by grahammechanical on 2015-11-04
If you are going to have a problem it will be with the video & WiFi drivers. The CPU is X86 but Ubuntu may not have drivers for the video and WiFi adapters. But then again you may not have a problem.

Regards.

---

### Post by vq1 on 2015-11-18
I would consider 2 alternative options:

1) buy a nexus 7 tablet for under 200 bucks that is ubuntu touch supported. 
2) Install virtual box or similar to run Ubuntu on your windows tablet

I am running Virtual Box and Lubuntu on a cheap nextbook Windows 10 tablet with only 1gb of ram. (I tried to get ubuntu running parallel but I was unsuccessful, no USB boot in BIOS).

---

