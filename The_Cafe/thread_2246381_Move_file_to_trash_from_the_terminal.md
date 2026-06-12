---
title: "Move file to trash from the terminal"
date: 2014-09-30
forum: The Cafe
---

### Post by pixelro on 2014-09-30
:p 

[https://www.youtube.com/watch?v=HjDf0xDm0xg](https://www.youtube.com/watch?v=HjDf0xDm0xg)

sudo apt-get install trash-cli
[man][http://manpages.ubuntu.com/manpages/natty/man1/empty-trash.1.html](http://manpages.ubuntu.com/manpages/natty/man1/empty-trash.1.html)

---

### Post by TheFu on 2014-09-30
Or just create an alias for rm.
[https://unix.stackexchange.com/questions/74213/how-to-change-rm-to-as-a-command-like-mv-trash](https://unix.stackexchange.com/questions/74213/how-to-change-rm-to-as-a-command-like-mv-trash)

**man bash** should explain aliases for that shell.  Most environments have aliases already - it is amazing what can be accomplished - so just find where yours are set and copy them. 

Be aware that on systems with many different file systems (unlike a trivial home system), this is a terrible idea and will likely lead to out of storage errors quickly. Plus moving files across file systems is really a copy/delete action, so NOT instantaneous.

OTOH, UNIX people tend to prefer files to be deleted when they tell them to be gone.

---

### Post by steeldriver on 2014-09-30
Gnome-based desktops should already provide the gvfs-trash CLI interface

---

### Post by pixelro on 2014-09-30
i can manually "trash" a file :> because it is stupid silly, just move the file in ~/.local/share/Trash[FONT=Ubuntu Mono]/[/FONT]files and add a ini file (*.trashinfo) something but nah trash-cli FTW :))

---

