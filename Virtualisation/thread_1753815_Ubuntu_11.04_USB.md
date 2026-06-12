---
title: "Ubuntu 11.04 USB"
date: 2011-05-09
forum: Virtualisation
---

### Post by AlexGeddylfson on 2011-05-09
I've searched the forums and I cannot come up with the answer. It keeps telling me that the USB subsyetem cannot be accessed. It's 32x Ubuntu 11.04 with the newest virtual box. I just want to share my movies and music with my xbox through my usb HD with a Windows VM.

---

### Post by Hedgehog1 on 2011-05-11
Greetings!

If your host OS is Ubuntu, you need to add your user to the 'vboxusers' group to be able to use USB from vbox:

[IMG]http://img190.imageshack.us/img190/5285/vboxusers.png[/IMG]

You may need to reboot after this change for it to take effect.

***The Hedge***

:KS

---

