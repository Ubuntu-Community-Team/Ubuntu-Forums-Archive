---
title: "Warcraft III having graphical anomalies in -opengl"
date: 2011-03-23
forum: Wine
---

### Post by Zirts on 2011-03-23
Hi,

So I have a problem with running WC3 in -opengl mode.

Basicly game starts up fine and so on,  but the graphics are very very weird.
It ain't so in D3D mode,  but in that mode the performance of that game is very very low considering the computer I use and the game I play.

Also as a side note,  other games like WoW and Modern warfare work just brilliant and with good FPS on the same computer.

Specs: 
Ubuntu 10.10
RAM: 4GB
Processor: AMD Athlon || Dual-Core
Video: Radeon HD 5650 1GB

Heres a picture of how it looks like in windowed mode:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=186902&stc=1&d=1300901614[/IMG]


Help would be appreciated.

---

### Post by Soulcage on 2011-03-24
Have you tryied disabling useGLSL? [http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys") You might need to try different drivers.

---

### Post by Zirts on 2011-03-24
I'm not really a expert too now so sorry for that, anyways I understand I need to go to regedit and change something there, but where do I really find that useGLSL,    didn't find anything about it on the link you provided.

And about drivers,   the opensource one that I had was not that good performance wize.   And when I go to the proprietary drivers menu I only see one option there for video card,  so I don't really know where I can find any more of thoes.


Edit>   Correction,   under Direct3D   there just inst such an option as useGLSL, so theres nothing to disable.

---

### Post by Soulcage on 2011-03-26
You have to add all the things to regedit.

---

### Post by Zirts on 2011-03-26
Okay, got it now,    I added that entry manually to regedit, but still I saw no difference, game had still thoes anomalyes in it :/.

---

