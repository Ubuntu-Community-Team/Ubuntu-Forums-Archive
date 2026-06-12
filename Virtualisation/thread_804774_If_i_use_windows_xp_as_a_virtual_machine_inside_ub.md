---
title: "If i use windows xp as a virtual machine inside ubuntu, will it use hardware as usual"
date: 2008-05-23
forum: Virtualisation
---

### Post by gottabeandrew on 2008-05-23
There's programs for windows only which i want to use but i don't want to go back to it so i'm thinking about installing windows xp as a virtual machine inside ubuntu using virtualbox. I'm using ubuntu 8.04.

Will windows xp be able to detect my laptop's hardware (mouse, earphones, webcam, video camera) just as it would if it were running normally or will all the settings have to go through ubuntu before they can get to windows xp (meaning that the ones which don't function right in ubuntu but would had i been running windows by itself wouldn't run properly in windows - if that makes sense).

Thanks for your time,

Andrew.

---

### Post by MeURi on 2008-05-23
Well, virtualization creates a sort of fake machine to install Windows to.

Some hardware will be your laptop's, some other not (e.g. video card, ethernet card); if a peripheral is connected through usb, it's likely to be seen as well in your Windows guest o.s. (if the virtual machine supports usb 'sharing' with the guest o.s.); integrated hardware is often emulated, I think for compatibility reasons

If I understand properly your concerns, you want to use through a virtual Windows what doesn't function properly under Ubuntu. Well, I think it's hard that such hardware will be ever seen by the guest o.s., not because it doesn't work under Ubuntu itself, but because of the fake machine that gets created to run the guest into

---

### Post by gottabeandrew on 2008-05-23
Ok, the best example i can give is that my webcam doesn't work on ubuntu by itself so i have to use this special program in ubuntu to get it to run. It has computer-based controls for moving it around and because this program in ubuntu doesn't have those controls, i can't move it around or zoom in or out. If i was using windows XP as a virtual machine inside ubuntu and i had the webcams program installed there, would i be able to move the webcam around and stuff just like i do normally?

---

### Post by maybeway36 on 2008-05-23
No, the virtual machine doesn't support your real hardware (including your webcam.)

---

