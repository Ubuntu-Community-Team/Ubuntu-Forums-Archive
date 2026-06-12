---
title: "Creating an icon to launch a wine app."
date: 2008-12-21
forum: Wine
---

### Post by toasty_ghosty on 2008-12-21
Hello,

I cannot seem to get this to work. I want to  launch WoW from an icon with the debugger on. Everything I have tried has not worked so far. I could be completely off though. Here is what I have tried:

/home/king/World\ of\ Warcraft/ WINEDEBUG="fixme-all" wine wow.exe

terminal /home/king/World\ of\ Warcraft/ WINEDEBUG="fixme-all" wine wow.exe

 env WINEDEBUG="fixme-all" wine "/World\ of\ Warcraft/wow.exe"

**I just moved over my WoW install from Windows. Hence the reason it is just sitting in my home folder. Everything runs fine when I launch it with just a command from the terminal:

WINEDEBUG="fixme-all" wine wow.exe

Any help?

---

### Post by soluphobe on 2008-12-21
Try setting your WINEPREFIX at the same time as your WINEDEBUG.  I think wine wants /home/$USER/.wine as it's default prefix, but you've just copy-pasted into a non-wine-sanctioned folder.  If you manually set WINEPREFIX to ~ or something it might work better (especially when hunting for data files).

---

### Post by Valok on 2008-12-22
When you make the launcher, you should be able to hit a 'browse' option on the window that pops up.  Once you get into there just navigate through the following:

/home/user/.wine/drive_c/Program Files/World of Warcraft

Once there you should be able to click on any of the .exe files and it will run it.

(ctr + h to show hidden files like '.wine')

---

### Post by toasty_ghosty on 2008-12-23
> WINEDEBUG="fixme-all" wine "/home/king/World Of Warcraft/Wow.exe"

Still doesn't want to work...any ideas why?

---

### Post by kostkon on 2008-12-23
Or you can just make a bash script like this
```
#!/bin/bash

## run WOW with debugging on
cd "/home/king/.wine/drive_c/Program Files/Microsoft Games/World Of Warcraft/";
WINEDEBUG="fixme-all" wine Wow.exe;
```
save it like *wowloader.sh* for example inside the WOW folder, make it executable, and then put in your launcher like this:
```
sh "/home/king/.wine/drive_c/Program Files/Microsoft Games/World Of Warcraft/wowloader.sh"
```

---

