---
title: "Wine prefix confusion"
date: 2009-02-10
forum: Wine
---

### Post by zami on 2009-02-10
Wine prefix confusion

I'm trying to set up a Popcap game in it's own wine directory, and it appears I've installed it there correctly, but it seems like it's using my default Wine settings when I actually run it, instead of that particular prefix/directories Wine settings.

I did in a terminal
export WINEPREFIX=$HOME/.wine-popcap
wineprefixcreate

then (in the same terminal)
cd Desktop
wine install.exe

then (still in the same terminal)
winecfg
and configured wine to run at 1024x768 virtual, with decorated windows.

I can see the .wine-popcap directory was created, and the game was installed there, but if I browse to the games' .exe it opens up looking like my default Wine settings - 1440x900 with no decorations.

What am I doing wrong?

-zami

---

### Post by zami on 2009-02-10
Just wanted to add...

if I am working in a terminal where I've done 
export WINEPREFIX=$HOME/.wine-lotro
and browse all the way to the game, and launch it with
wine play.exe
it does launch with the correct winecfg settings.

But if I use nautilus to browse to it, and just right click and open it with "open with Wine" (or whatever the wording is), it opens with my default winecfg settings.

Hopefully someone can explain what I'm doing wrong, and maybe how to make shortcuts that will use the correct winecfg.

Thanks!

-zami

---

### Post by cogadh on 2009-02-10
You need to specify the wineprefix when you run the Wine commands, otherwise it uses your default .wine directory and its settings, regardless of where the executable actually is located. When running those commands, you need to do this:
```
env WINEPREFIX="/home/<username>/.wine-popcap" wine install.exe
env WINEPREFIX="/home/<username>/.wine-popcap" winecfg
env WINEPREFIX="/home/<username>/.wine-popcap" wine "C:\Program Files\path\to\game\game.exe"
```

---

### Post by zami on 2009-02-10
cogadh, you are my hero for the day!!:guitar:

That worked perfectly.

```

env WINEPREFIX="/home/laura/.wine-popcap" wine "c:\Program Files/PopCap Games/Insaniquarium Deluxe/Insaniquarium.exe"

```

(Now if I can just figure out why it's resizing to 800x600... my son is going to flip his little lid.)

Thanks so much.

-zami

---

