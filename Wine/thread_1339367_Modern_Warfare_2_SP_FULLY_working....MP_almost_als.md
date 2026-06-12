---
title: "Modern Warfare 2 SP FULLY working....MP almost also but a &quot;small&quot; detail...."
date: 2009-11-27
forum: Wine
---

### Post by AJSB on 2009-11-27
Singleplayer FULLY working....MULTIPLAYER almost...NEED YOUR help !

OK, i managed to put the SP fully working (details later), mainly thanks to 48khz, ALSA, 16bit and the patch....all this in XUBUNTU 9.10.

As for MP , i played online (AFAIK, in a VAC server !) today but i give it up for now, because a "small" problem....NO SOUND at all.

If i use same settings than for SP, MP crashes at start up....i have to change in Wine from ALSA to OSS to not crash but then i have no sound !!! :(

Notice that also in COD2 and COD4, i used under Slackware 12.2, ALSA for SP and OSS for MP to avoid also the start up crashes, but in both cases i had sound !


Any ideas ?!?....Slackware 13 ?!? :P

TIA,
AJSB

---

### Post by AJSB on 2009-11-27
OK , i found it by myself....it seems that i needed alsa-oss package and put aoss before "env=....." (i.e. "aoss env=.....")

Will test it fully tonight....then i put here or wine AppDB a full report.

---

