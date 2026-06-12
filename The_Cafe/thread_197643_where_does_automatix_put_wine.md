---
title: "where does automatix put wine"
date: 2006-06-16
forum: The Cafe
---

### Post by Drifter on 2006-06-16
when u install wine with automatix where does it put.

---

### Post by Anduu on 2006-06-16
It should be in /home/username/.wine

Makes sure to ctrl+h to show hidden files.

---

### Post by Drifter on 2006-06-16
It is not in home username, I did use control H.  What other possibilities where it could be.

---

### Post by FISHERMAN on 2006-06-16
I don't know exactely what you mean(more information!), but I'm guessing that you don't know how to start wine(if this isn't the cause, you might as well ignore this post). 
But just right-click on a an *.exe and choose "open with" "different application"
Don't choose anything from the list. instead you should take "open with an specific command" type **wine** .If wine is installed correctly(and the *.exe works with wine) it should work(the parts between " " are translated from Dutch so they might not be identical to the English original).

---

### Post by Drifter on 2006-06-16
I not only didn't know how to run it, I can't find where automatix put.  What folder or dir. it is in.  It is not in home user where most people say it should be.  How can I find it.

---

### Post by Somenoob on 2006-06-16
Search for it with a terminal

```
Locate wine
```

---

### Post by truoc444 on 2006-06-16
did you set it up

$ winecfg

without running that command wine installed by Automatix is useless.

---

### Post by Drifter on 2006-06-16
[QUOTE=truoc444]did you set it up

$ winecfg

without running that command wine installed by Automatix is useless.[/QUOTE]
When u run winecfg is this all u need to do for wine to work or is there someother things u need to do.

---

### Post by PatrickMay16 on 2006-06-16
Once you've run winecfg, find some windows executable .exe that you'd like to run, then in the terminal do this:

wine path/to/file/file.exe

or this (recommended)

cd path/to/file/
wine file.exe

This should do the trick. You should be fackin' like a master with wine in no time.

---

