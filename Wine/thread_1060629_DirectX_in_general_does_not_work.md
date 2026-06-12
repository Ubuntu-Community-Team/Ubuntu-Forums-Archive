---
title: "DirectX in general does not work"
date: 2009-02-04
forum: Wine
---

### Post by Furyhunter on 2009-02-04
Strangely enough, DirectX applications (WoW 3.0.1, namely) seemed to work absolutely flawlessly until recently... I'm not sure what caused it.

Basically, any DirectX9C application I run, no matter the settings, gives a corrupted cursor icon and either freezes in the case of most applications or, in WoW's case, pops open an exception.

Games listed as "Gold" or "Platinum", including Eve Online, do not work at all because of this. Even the official Eve "Linux Client" doesn't work, do to... erm, various reasons.

I am using an nVidia 9800GT from EVGA, standard specification, and using the 180 proprietary driver. WoW works perfectly with -opengl. Generally no other problems.

---

### Post by cogadh on 2009-02-05
DId you do anything like install the actual DirectX over Wine's DirectX?

---

### Post by Furyhunter on 2009-02-05
That might have been what I did. Windows installers like to do things behind my back... Should I remove .wine and reconfigure? (All of my Windows stuff is on a separate Windows-based drive entirely, so no need to backup drive_c)

Edit: No... doing that did not solve it, even after a reboot.
Edit2: Nope, there is something. EVE Online gives a black screen, but that's about it. I haven't tried any tweaks suggested on appdb.

---

