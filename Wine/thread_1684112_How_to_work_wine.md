---
title: "How to work wine"
date: 2011-02-08
forum: Wine
---

### Post by cblnchat on 2011-02-08
Im having problems with wine.  I cant seem to figure out how to work it.  Ive never used it before and the only thing ive tried to open is N Game.  And it just wont open.  

Thanks

---

### Post by dino99 on 2011-02-09
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

---

### Post by P4man on 2011-02-09
> **cblnchat said:**
> Im having problems with wine.  I cant seem to figure out how to work it.  Ive never used it before and the only thing ive tried to open is N Game.  And it just wont open.  

Thanks


Try starting it from the commandline, so you can see what the problem is

wine /path/to/your/windowsgame.exe

You probably need some windows libraries, or stuff like DirectX. Easiest to install that is winetricks:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by cblnchat on 2011-02-25
> **P4man said:**
> Try starting it from the commandline, so you can see what the problem is

wine /path/to/your/windowsgame.exe

You probably need some windows libraries, or stuff like DirectX. Easiest to install that is winetricks:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

Ill try that.  But when i click on the .exe nothing happens.  And when i do the command line again not much happens.  But im still new to the command line so i could be doing something wrong.

---

### Post by P4man on 2011-02-26
> **cblnchat said:**
> Ill try that.  But when i click on the .exe nothing happens.  And when i do the command line again not much happens.  But im still new to the command line so i could be doing something wrong.

copy paste the "nothing much" here, so we can see what you are doing or doing wrong, and what the error is.

---

### Post by apostra on 2011-02-27
silly question, 
but have u made executable? Right click->properties->permission->Allow executing as program
Ofc at Open with tab wine should be selected

---

