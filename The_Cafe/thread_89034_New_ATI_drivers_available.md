---
title: "New ATI drivers available"
date: 2005-11-11
forum: The Cafe
---

### Post by dolny on 2005-11-11
I just visited the ATI.com site and found out that new drivers have been released.

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)

---

### Post by quietglow on 2005-11-11
I just tried the installer and it hosed my xconf. I'm still trying to figure out what's up but it looks like the fglrx module didn't load properly...

Really stock (non 64) Breezy running on an AMD 64 machine and an X300 chipset card, by the way.

---

### Post by WildTangent on 2005-11-11
[QUOTE=quietglow]I just tried the installer and it hosed my xconf. I'm still trying to figure out what's up but it looks like the fglrx module didn't load properly...

Really stock (non 64) Breezy running on an AMD 64 machine and an X300 chipset card, by the way.[/QUOTE]
Woah! how'd you get that to work? I've got the same setup, and RS480 chipset, but mine doesnt work :P X won't start

-Wild

---

### Post by quietglow on 2005-11-11
Naw, X won't start for me either. That does save me posting wondering if it's working for anyone else though :-)

I'm still no 3d on my 23" Cinema Display that really want to be showing some Cube shootin'! Can't wait to hear if someone gets this workin'.

---

### Post by zachtib on 2005-11-11
the 8.16.20 drivers work fine for me

---

### Post by dolny on 2005-11-12
Not for me. Besides occasional computer freezes, Day of Defeat or Half Life 1 on Steam works terribly. Half Life is playable - but on 1024x768 the frames are between 16-55, but Day of Defeat: 5fps - 15 (mainly 5) - totally unplayable.

glxgears output is over 3000 FPS

My system specs: 
ATI Radeon 9600 Pro (yeah... :/ ATI...)
Celeron 2.8 Ghz
512 DDR RAM (2x256)
Ubuntu Linux - Breezy Badger, KDE 3.2B
Cedega 5.0 (It was working as bad on 4.4.1, 4.4.3)

I tried changing xorg.conf many times and in many ways. Nothing helps. I have no fastwrites and AGP x2, x4, x8 options in my BIOS :| Ati Control in KDE shows: 

"Transfer mode: AGP x8, SBA, FW (I tried disabling and enabling them through Windows - either way its slowww), AGP v3.0 native mode"

Does this mean that my AGP is NOW working in x8 mode or it shows the maximum possible card speed?

Can somebody with similar specs paste his xorg.conf?
HELP?!

---

