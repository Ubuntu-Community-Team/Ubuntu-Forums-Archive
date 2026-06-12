---
title: "DVD's on wine"
date: 2010-12-23
forum: Wine
---

### Post by Spyderkid on 2010-12-23
how can I install a DVD from the .exe file on wine.

When I try to make it "allow executing as a program" it says its a read only filesystem and can't be changed it does this with all DVD/ROM's


I know you can faff with windows or virtual boxes and then do something or other to make it work but i'd rather not.

---

### Post by ridetheteapot on 2010-12-23
whats going on is all nautilus.

its using /usr/bin/cautious-launcher to launch exe's. just change the nautilus launch option, or launch from terminal.

---

### Post by Spyderkid on 2010-12-25
i'm sorry but how do you change the nautilus option? and which option would that be?

---

### Post by Spyderkid on 2010-12-26
i'm sorry but how do you change the nautilus option? and which option would that be?

bump

---

### Post by Spyderkid on 2010-12-26
How do I change the settings on nautilus

---

### Post by ridetheteapot on 2010-12-28
sorry -
right click the bin and select properties - then go to 'open with'
and change (or make a new entry to /usr/bin/wine)

---

### Post by Spyderkid on 2010-12-29
Do you mean the rubbish bin or the folder bin?

---

### Post by ridetheteapot on 2010-12-30
bin - i mean binary

---

### Post by cogadh on 2010-12-31
Easier to just open a terminal, change directories to the DVD, then "wine" the executable:
```
 cd /media/whatever
wine setup.exe
```

---

### Post by Spyderkid on 2011-01-05
I tried to cd to the DVD but this happened im not quite sure how to cd to it...

```

bob@Ubuntu:~$ cd media
bash: cd: media: No such file or directory
bob@Ubuntu:~$ cd media/SPEEDYEGGBERT
bash: cd: media/SPEEDYEGGBERT: No such file or directory
bob@Ubuntu:~$ 

```

---

### Post by cogadh on 2011-01-05
Looks like you are simply using the wrong path:

```
cd /media/SPEEDYEGGBERT
```

That leading "/" is important.

---

### Post by Spyderkid on 2011-01-06
thank you very much Cogadh!

I did need to add in the '/' at the begging and the installation worked fine, now is just to see how well it works with wine :D :D :D

---

### Post by Spyderkid on 2011-01-06
Turns out that DVD doesn't work great on wine at all but it installs ok.

But I got loads more to try out and thanks for telling how to do it.

---

### Post by Spyderkid on 2011-01-07
Need help on which file to "wine".
(setup.exe didn't work)

There is:...

Setup.now.exe
setup.exe
AUTORUN.EXE

should I try any others I'm using the command
[FONT="Courier New"]Wine [name].exe[/FONT]

for the setup.exe i ran [FONT="Courier New"]wine setup.exe[/FONT] as you would expect

---

