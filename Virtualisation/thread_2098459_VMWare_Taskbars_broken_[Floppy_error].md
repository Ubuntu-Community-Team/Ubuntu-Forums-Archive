---
title: "VMWare: Taskbars broken? [Floppy error]"
date: 2012-12-26
forum: Virtualisation
---

### Post by emwo on 2012-12-26
Hi! Newbie question, I think. I have Windows 7 (x86) and I'm installing Ubuntu (12.04) in VMware and at first it gave me a floppy mounting error... so I created an image and reinstalled the OS. After it reinstalled it didn't give me an error, but the OS is  still virtually unusable. I can log in fine, I can see the background but I can't see the taskbars and pressing alt + f2 shows a black screen and flickers the background. 

There's a broken image for the left side of the taskbar, and I can still use the drop down menus at the top. [IMG]http://i.imgur.com/o9dvF.png[/IMG]

Is it a virtualization issue or a driver issue? I can't manage to open the terminal or any application beyond libreoffice/firefox :\


also, I don't know what I opened by randomly clicking around but I got [IMG]http://i.imgur.com/jk1dm.png[/IMG] error too. Halp? D:

---

### Post by dcstar on 2012-12-28
> **emwo said:**
> Hi! Newbie question, I think. I have Windows 7 **(x86)** and I'm installing Ubuntu (12.04) in VMware
.........

Why do people use crap 32-bit software..... never mind.....

[LIST=1]
[*]Go into the VM settings and turn off the Accelerate 3D Graphics option and see if that makes a difference.
[*]Install VMware Tools on the VM.
[/LIST]

---

### Post by emwo on 2012-12-29
Turning off 3D Graphics did it. >__< Thanks

---

