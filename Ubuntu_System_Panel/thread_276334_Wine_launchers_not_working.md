---
title: "Wine launchers not working"
date: 2006-10-12
forum: Ubuntu System Panel
---

### Post by Cynical on 2006-10-12
I play counter-strike and use ventrilo. Neither those nor the steam shorcut I setup work with the Ubuntu System Panel. They are correct and work fine with the main menu. Has anyone else experienced this problem or am I alone?

---

### Post by chanders on 2006-10-13
What are the commands you use to execute the game? I think someone had a similar problem but they got it solved eventually due to some of the command line arguments...

---

### Post by Cynical on 2006-10-13
For steam:
wine C:/Program\ Files/Steam/Steam.exe WINEDEBUG=fixme-all

and for cs:
wine C:/Program\ Files/Steam/Steam.exe -fullscreen \ -width 1280 -height 1024 -applaunch 10 \ -heapsize 512000 +map_background none "$@"

They work fine with the regular menu thats what surprised me. Another strange thing is that even though they should be in the Games submenu (and they are when I open alacarte), they show up in accessories when trying to find them manually in usp.

---

### Post by mucha on 2006-10-14
Try to make a new file in /usr/local/bin and write:

```
#!/bin/bash
wine C:/Program\ Files/Steam/Steam.exe WINEDEBUG=fixme-all
```

Then give it write permissions (chmod +x file).
And theeen add the new startfile to USP

---

### Post by PWill on 2006-10-16
This works for me for Steam:
```
wine "C:\Program Files\Steam\steam.exe"
```

---

### Post by cdfs on 2006-10-16
The Problem is the submenu... USP can't handle submenus at the moment. I asked nearly the same some days ago. Chanders said, he will include this functionality in a former version of USP but not now, as there is lots of other stuff to be done.

CDFS

---

### Post by mucha on 2006-10-17
What would that have anything to do with the launchers from the applicationspane? That only effects the coding of plugins as far as I know.

---

