---
title: "Console Bell (Beep) Not Working in 8.04"
date: 2008-06-28
forum: System76 Support
---

### Post by compholio on 2008-06-28
Well, I finally upgraded my SERP3 to 8.04 (32-bit) and after tweaking some things I'd done to GRUB and the nVidia driver I seem to have a fully functional system except for one issue: the console bell is not working.

After I first upgraded the console bell was extremely loud and obnoxious, so I ran the System76 driver in the hope that that would fix it.  After I rebooted I found that I can no-longer get the console bell to go off at all.  I have checked that pcspkr is loaded, that the "Enable system beep" is checked in GNOME, that "Terminal bell" is enabled in gnome-terminal, and that the length and frequency of the bell are non-zero.  So, I'm scratching my head here a bit wondering why I don't have a beep, especially since the beep is not working on my virtual consoles either.  Any help with this issue would be greatly appreciated.

---

### Post by thomasaaron on 2008-06-30
It's gone on my computer too.

Not too long ago, someone was complaining about the beep because it couldn't be adjusted/turned off. Turned out it was a feature that hadn't been developed fully and thus had bugs filed against it.

Looks like maybe they removed the feature all together to stop complaints until that get it fixed.

---

