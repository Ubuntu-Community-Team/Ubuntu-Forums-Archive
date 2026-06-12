---
title: "Shortcut to program in wine, halp."
date: 2009-12-03
forum: Wine
---

### Post by jessiebrownjr on 2009-12-03
I'm sure this question has been seen before, but for the life of me, I can't make it work.
I have tried launching it a few different ways but the only way I can do it is to go into the directory and either right click/run as wine app, or just select it and hit enter.. I would LOVE a shortcut to my desktop...

---

### Post by ajgreeny on 2009-12-03
This is probably a result of the pathway to the executable containing spaces, so put the full pathway in "pathway" quotes or use a backslash at the start of the space, leaving the space still in place.  As examples:-

wine [COLOR=Red]"[/COLOR]/home/user/.wine/drive_c/Program Files/Prog folder/file.exe[COLOR=Red]"[/COLOR]
or
wine /home/user/.wine/drive_c/Program[COLOR=Red]\[/COLOR] Files/Prog[COLOR=Red]\[/COLOR] folder/file.exe

---

### Post by jessiebrownjr on 2009-12-03
> **ajgreeny said:**
> This is probably a result of the pathway to the executable containing spaces, so put the full pathway in "pathway" quotes or use a backslash at the start of the space, leaving the space still in place.  As examples:-

wine [COLOR=Red]"[/COLOR]/home/user/.wine/drive_c/Program Files/Prog folder/file.exe[COLOR=Red]"[/COLOR]
or
wine /home/user/.wine/drive_c/Program[COLOR=Red]\[/COLOR] Files/Prog[COLOR=Red]\[/COLOR] folder/file.exe

Thanks for the reply, but I figured this might be the case, and I have removed all the spaces.. Now I have a weird reply to my own post.. for SOME REASON.. I was able to drag the shortcut to gnome-do with the Docky appearance on.. and IT WORKS.... this is almost a victory, but not what I was going for..

---

### Post by andrea000 on 2009-12-05
I'M sure you have tried to just pull the program
down from the wine menu but try that if you have
not.Also this may help create a launcher and go
to command to launch replace that command with
this replacing the Rosetta stone with the software
your trying to run.

> nv WINEPREFIX="/home/me/.wine" wine "C:\Program Files\Rosetta Stone\Rosetta Stone V3\RosettaStoneVersion3.exe"

---

### Post by Leighman on 2009-12-05
env*

---

