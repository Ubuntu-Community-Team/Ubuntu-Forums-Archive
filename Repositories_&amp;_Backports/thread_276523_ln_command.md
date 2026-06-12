---
title: "ln command"
date: 2006-10-13
forum: Repositories &amp; Backports
---

### Post by ckonrad on 2006-10-13
i am trying to install the jre right now and the instructions call for using an ln -s command and it just isnt recognized by my terminal, is there a way i can make sure i have all the commands in linux so i dont have to ask everytime i run into these kinds of issues?


Thanks

---

### Post by JonahRowley on 2006-10-13
You really should have ln.  I can't think of a reason you wouldn't have it.  Just to be sure, that's ell-enn, right?  Not capital eye-enn?

Type 'which ln', and you should get /bin/ln.  It's part of the fileutils package, which you really cannot function without.  BTW, I think automatix installs the JRE for you, it's a lot easier than installing it manually.

---

### Post by ckonrad on 2006-10-13
> **JonahRowley said:**
> You really should have ln.  I can't think of a reason you wouldn't have it.  Just to be sure, that's ell-enn, right?  Not capital eye-enn?

Type 'which ln', and you should get /bin/ln.  It's part of the fileutils package, which you really cannot function without.  BTW, I think automatix installs the JRE for you, it's a lot easier than installing it manually.

yeah i have ln the entire problem was just that i was typing ln -s/usr.....
intead of of ls -s /usr with the space. That is the thing with command lines they might be more efficient but its impossible to make a mistake like that in a Gui.

I think i will use automatix i followed the directions to install the jre and it still inst detecting java web content, i really dont see why.

I like your dr orphius picture i have all the venture episodes fricken hilarious stuff.

---

### Post by JonahRowley on 2006-10-13
Command-line has a learning curve.  Once learned, you can do far more than any GUI.  Also, you might need to do something to get firefox to find the java plugin.  I don't use Java, so I really can't help you there, but look in about:plugins for a start.

Thanks, I saw that image and knew it had to be my avatar ;)

---

