---
title: "wine says not executable, wine is wrong"
date: 2010-06-24
forum: Wine
---

### Post by FFGANDALF on 2010-06-24
I'm getting the following message when I try to open .exe files in wine,

> The file '/media/Storage/Games/WEP/SKI.EXE' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

now the first thing I did was ls -l /media/Storage/Games/WEP/SKI.EXE which gave me an output of > -rwxr-xr-x 1 USERNAME_GENERIC USERNAME_GENERIC 88848 2007-01-02 15:56 /media/Storage/Games/WEP/SKI.EXE

so according to ls i already have the executable bit set.
I then tried several other executables with the same result. After reinstalling wine the problem has persisted, any ideas?

---

### Post by launchy on 2010-06-24
try right click on the item, and in permissions check allow executing file as program

---

### Post by FFGANDALF on 2010-06-25
already tried that, according to nautilus it's already set to be executable.(as evidenced also by the ls output)

---

### Post by hikaricore on 2010-06-25
Just run it from a terminal then.
Gnome/nautilus' built in wine protection can't stop you from running anything there.

---

