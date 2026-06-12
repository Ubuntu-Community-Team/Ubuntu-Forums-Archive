---
title: "WoW On hard drive? (ubuntu 10.4)"
date: 2010-06-24
forum: Wine
---

### Post by TommyfoarRoshie on 2010-06-24
Im a wow addict and am wondering can i run wow through wine without installing it on the linux partition just getting it from the windows partition? is that possible and how would i run it through wine?

---

### Post by donkyhotay on 2010-06-24
You should post this on the [ ubuntu wine subforum](http://ubuntuforums.org/forumdisplay.php?f=313) rather then gaming. To answer your question though you'll break things if you try. Although the files are there and intact it will mess up the registry. It is always best to install with wine, sometimes you can copy the program files directly from windows into wine and get it to work but you should at least copy into the wine folder, don't run directly from a windows partition.

---

### Post by VH-BIL on 2010-06-24
I have done this with other games with no problems. A lot of windows games will recreate the registry entries if they are not found.

---

### Post by TommyfoarRoshie on 2010-06-25
i copied and pasted the file into the ubuntu side of the partition =D
so do i put it in program files or the wine part?

---

### Post by hikaricore on 2010-06-25
You can honestly put it whereever you like, just as long as you know where it is and point any shortcuts you might have to the right location. :p
One little tidbit of warning...
The blizzard updater has been known to cause file permissions **disasters** in the past so be aware of this if something goes wrong after an update.
Usually this is localized to the warcraft directory and only it needs fixed, but I have seen cases where a person ran an update binary from their home folder and it screwed up the file permissions of the entier directory.  >.>
Anyway this may have been fixed but I thought you should know.

---

