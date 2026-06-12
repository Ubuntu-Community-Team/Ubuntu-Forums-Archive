---
title: "Why wont my launcher work!!!!???"
date: 2010-11-08
forum: Wine
---

### Post by iluii on 2010-11-08
I am going crazy, im trying to launch AOE2 (i know its old but my pc is no very powerful ... dont judge me monkey) and it is just not working. 

the game resides here:
~/.wine/drive_c/Program Files/Age of Empires II/Age2_x1 

and the exe file is called Age2_x1.exe

if I open a terminal and do this:
francisco@francisco-laptop ~/.wine/drive_c/Program Files/Age of Empires II/Age2_x1 $ wine age2_x1.exe

the game launches fine

but if I open a terminal and do this:
francisco@francisco-laptop ~ $ wine /home/francisco/.wine/drive_c/Program\ Files/Age\ of\ Empires\ II/Age2_x1/age2_x1.exe

 nothing happens! :confused:  I just get the following:
francisco@francisco-laptop ~ $
No error messages or anything
 
this means my launcher obviously doesn't work either
did I misspell something ? this is kinda driving me crazy, any help and all is appreciated

---

### Post by or3x on 2010-11-08
Try using ""
"~/.wine/drive_c/Program Files/Age of Empires II/Age2_x1.exe"
Ubuntu usually doesn't like blank spaces

---

### Post by iluii on 2010-11-08
maybe im misplacing the " "

but terminal says

francisco@francisco-laptop ~ $ wine "/home/francisco/.wine/drive_c/Program\ Files/Age\ of\ Empires\ II/Age2_x1/age2_x1"
wine: cannot find '/home/francisco/.wine/drive_c/Program\ Files/Age\ of\ Empires\ II/Age2_x1/age2_x1'

---

### Post by iluii on 2010-11-08
eliminate the backslahes DUH

but anyway

francisco@francisco-laptop ~ $ wine "/home/francisco/.wine/drive_c/Program Files/Age of Empires II/Age2_x1/age2_x1.exe"
francisco@francisco-laptop ~ $ 


got nothin

---

### Post by or3x on 2010-11-08
Then I don't really know what could be wrong

---

### Post by iluii on 2010-11-08
> **or3x said:**
> Then I don't really know what could be wrong

I know right?:confused: Very frustrating , thanx anyway

guess ill just browse to the folder and start it that way! :(

---

### Post by _outlawed_ on 2010-11-08
```
wine "/home/francisco/.wine/drive_c/Program\ Files/Age\ of\ Empires\ II/age2_x1.exe"
```

---

