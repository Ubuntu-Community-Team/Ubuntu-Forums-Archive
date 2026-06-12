---
title: "I'm trying to create a launcher on panel for a wine app"
date: 2010-11-17
forum: Wine
---

### Post by LutraMan on 2010-11-17
This command works via terminal:
```
WINEPREFIX=~/.wine-winamp wine 'C:\\Program Files\\Winamp\\winamp.exe'
```

but when I copy it to the launcher command box and try to launch it I'm getting the following error:
Could not launch application
Failed to execute child process WINEPREFIX=~/.wine-winamp (no such file or directory)

anyone knows what should I do?

---

### Post by ajackson on 2010-11-17
Stick **env** in front of it ie:
```
env WINEPREFIX=~/.wine-winamp wine 'C:\\Program Files\\Winamp\\winamp.exe'
```

---

### Post by LutraMan on 2010-11-17
I thought you may say this :P

well, 1st of all tnx. but I tried it already B4 and though it didn't gave me an error, it also did not load up the program.

BTW, what does env supposed to do?

and if you have anymore ideas, even if it's just to check something, let me know, I'm willing to try.

---

### Post by ajackson on 2010-11-17
It might be because you start the path with ~, try changing that to the the proper /home/username. If that doesn't work I'm out of ideas :)

---

