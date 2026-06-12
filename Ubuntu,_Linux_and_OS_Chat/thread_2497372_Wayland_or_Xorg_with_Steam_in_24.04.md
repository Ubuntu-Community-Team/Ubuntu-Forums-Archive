---
title: "Wayland or Xorg with Steam in 24.04?"
date: 2024-05-02
forum: Ubuntu, Linux and OS Chat
---

### Post by kinderfeld on 2024-05-02
Curious which I should be using with Steam. Wayland is new to me and Steam as well (at least on Linux anyway). Lots of reddit comments say used Xorg, but noticed I couldnt get Witcher 3 to run when using Xorg, but plays great when using Wayland. So yea, looking for some advice.

BTW, video card is an AMD RX 6800XT

---

### Post by DuckHook on 2024-05-03
I have a really oddball custom setup in which Steam runs within a container. I am unable to get it to run in Wayland, but it runs okay in Xorg. In fact, none of my graphical apps will run within a container under 24.04 Wayland. I have to use Xorg.

Hopefully, this gets solved soon because I've moved on from Xorg for a couple of years now. And yes, my containerized graphical apps run fine is 22.04, so it's definitely something that happened in 24.04. Actually, it started happening in 23.10, but I expect wonkiness from standard releases whereas I expect better usability from LTS releases.

Short answer is: use what works. Wayland is nice because it is more secure and is actively being worked on and maintained. Xorg's days are numbered.

This puts me in more of a pickle than you since I'm the one who must run an aging soon&#8209;to&#8209;be&#8209;obsolete platform to keep things working. If Wayland works for you, then you are current and should be happy.

---

