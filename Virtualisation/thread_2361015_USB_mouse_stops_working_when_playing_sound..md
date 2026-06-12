---
title: "USB mouse stops working when playing sound."
date: 2017-05-11
forum: Virtualisation
---

### Post by forlackofabettername on 2017-05-11
This has got to be one of the weirdest problems I have ever had. Here's my setup:


[LIST]
[*]Ubuntu 17.04 + Gnome (running in qemu 2.8.0)
[*]Nvidia GTX 980 TI (passed through to VM, using proprietary drivers)
[*]PCIe USB 3.0 expansion card (passed through to VM)
[LIST]
[*]Logitech MX Master (receiver plugged into expansion card)
[*]USB keyboard (plugged into expansion card)
[*]USB sound card
[/LIST]
[/LIST]

Everything works fine when I am doing light tasks, e.g. web browsing, coding, etc. As soon as I start doing anything that causes even moderate GPU load (edit: actually, whenever it tries to play any sound), my mouse stops working. This includes playing YouTube videos or launching Steam games. I have tried unplugging/replugging the receiver, using bluetooth instead of the Logitech receiver, and using a different port. None of these work. After closing the video or game, the mouse starts working again after a few seconds. The keyboard and other devices plugged into the same USB expansion card work fine.

I have checked dmesg and Xorg logs. There's nothing related to the mouse being disconnected or reconnected (except when I unplugged/replugged the receiver).

Where else should I check to continue troubleshooting?

Edit: It's NOT the graphics card. The issue seems to be caused by a USB sound card plugged into the PCIe USB expansion card. The fact that it was failing when loading up games and videos made me assume it was an interaction with the graphics card. In both cases, the computer's also trying to play sound :)

Found a couple of related forum posts, but no answer:
[URL="https://superuser.com/questions/1103759/how-do-i-fix-mouse-freezing-when-sound-playback-is-active-on-debian"]https://askubuntu.com/questions/773369/mouse-doesnt-work-while-audio-is-playing
https://superuser.com/questions/1103759/how-do-i-fix-mouse-freezing-when-sound-playback-is-active-on-debian[/URL]

---

