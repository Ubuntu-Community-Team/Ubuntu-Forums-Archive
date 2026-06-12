---
title: "Paint Shop Pro 9 with  Wine"
date: 2008-12-05
forum: Wine
---

### Post by DLF44 on 2008-12-05
i just installed ubuntu 8.10 and am looking to get paintshop pro 9. 
is it possible to use wine to run paintshop pro 9? 
ive got it downloaded but not sure what to do next.

---

### Post by ajmorris on 2008-12-06
hi there,
it *may* be possible to run it, many versions of photoshop run as well, so that is an alternative for you. But basically, to install paint shop pro in wine, open a terminal, and navigate to the directory that you downloaded the paint shop pro install executable to. Then run (if not already installed):
```
sudo apt-get install wine
```

then:
```
wine paintshop-pro-9.exe
```

follow the install, and then try to run it from either the menus, or using the wine command on the executable in ~/.wine/drive_c/Program\ Files/<wherever paintshop pro is installed>/paintshop-pro.exe

If it runs, then you can celebrate, otherwise, you will probably have to do some searching on the internet for some methods on installing this particular application in wine (for example getting some native windows system libraries). 



AJ

---

### Post by DLF44 on 2008-12-07
alright, i got wine installed as well as psp 9 
it opens and i can use most features, but the problem is i cant save anything, or open anything.
any ideas?

---

### Post by ajmorris on 2008-12-07
> **DLF44 said:**
> alright, i got wine installed as well as psp 9 
it opens and i can use most features, but the problem is i cant save anything, or open anything.
any ideas?

please open up a terminal, and navigate to ~/.wine/drive_c/Program\ Files/<phosthop install dir>/
then run wine <.exe>  where .exe is the photoshop executable to run the application.


Then paste here the entire ouput from the terminal, when you try to save/open files. (please use [CODE] envelops around the output, as by default wine prints debug messages to the terminal, so this output might be quite long...)


AJ

---

### Post by DLF44 on 2008-12-08
hey im not sure what you meant by this

"please open up a terminal, and navigate to ~/.wine/drive_c/Program\ Files/<phosthop install dir>/
then run wine <.exe> where .exe is the photoshop executable to run the application.

i opened up terminal and paintshop pro 9, but the error messages wernt showsing up in terminal

sorry i probly misunderstood

---

### Post by bwang on 2008-12-09
You have to run the program from the terminal! Do so by typing wine <name of executable> from the terminal and hitting enter.

---

### Post by DLF44 on 2008-12-11
ok this is what i got when i typed it.

```
dlf@dlf-laptop:~$ wine <Paint Shop Pro 9.exe>
bash: syntax error near unexpected token `newline'

```

---

### Post by murrayd77 on 2008-12-12
Run PSP 9.0 from terminal and hope it will run. If still you get error messages, try removing PSP and reinstall it again. It might run without any issues. 

-- Dave.

---

### Post by DLF44 on 2008-12-15
hey, i will still not run. but im also having trouble removing it now.

i click 
applications
wine
then go to the psp folder and click uninstal and nothing happens.

is there another way to remove it?

---

### Post by Nico-dk on 2008-12-17
Bumping this, because I'll be in need of doing this in a few days too.
Linux seriously need some good competiton for the plethoa of win gfx apps ;)

---

### Post by DLF44 on 2008-12-18
bump.
anyone have any suggestions?

---

### Post by jrusso2 on 2008-12-18
Try Krita, thats a pretty good app.

---

### Post by Nico-dk on 2008-12-19
Oooh, that actually looks interesting and useful, thanks for sharing :)

---

