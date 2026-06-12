---
title: "PlayOnLinux passing mysterious variable..."
date: 2010-03-20
forum: Wine
---

### Post by J V on 2010-03-20
When I run a playOnLinux script straight off, Anarchy Online runs perfectly (Better than windows, except, yknow, it crashes when it goes off screen so no dragging or switching workspaces)

Problem is that running the same script through PlayOnLinux makes the game render like crap, so I was wondering what the difference is? From what I can tell theres only one variable POL passes to the script, but IDK what it does, can anyone explain?

```
#!/bin/bash
PATH="/home/j/.PlayOnLinux/WineVersions/1.1.40/usr/bin/:$PATH" # /me thinks problem is here, have removed most of script other than this and added back one at a time...
export WINEPREFIX="/home/j/.wine/"
export WINEDEBUG="-all"
cd "/home/j/.wine/drive_c/Program Files/Funcom/Anarchy Online/"
gconftool -t bool -s /desktop/gnome/peripherals/keyboard/repeat false
wine "/home/j/.wine/drive_c/Program Files/Funcom/Anarchy Online/Anarchy.exe" >/dev/null 2>&1
```

---

### Post by Brebs on 2010-03-20
Look in the obvious directory:

ls -l /home/j/.PlayOnLinux/WineVersions/1.1.40/usr/bin/

---

### Post by J V on 2010-03-20
I just don't understand the syntax... When I just sh the script it runs fine but when POL runs it it passes (presumably) the $PATH variable and changes it...

ls /home/j/.PlayOnLinux/WineVersions/1.1.40/usr/bin/
function_grep.pl  widl       wineconsole  wineg++    wineprefixcreate
msiexec           wine       winecpp      winegcc    wine-preloader
notepad           wineboot   winedbg      winemaker  wineserver
regedit           winebuild  winedump     winemine   wmc
regsvr32          winecfg    winefile     winepath   wrc

---

