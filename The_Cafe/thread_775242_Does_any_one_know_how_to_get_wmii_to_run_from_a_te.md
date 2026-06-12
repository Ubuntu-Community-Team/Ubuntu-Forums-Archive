---
title: "Does any one know how to get wmii to run from a terminal"
date: 2008-04-29
forum: The Cafe
---

### Post by Lostincyberspace on 2008-04-29
Does any one know how to get wmii to run from a terminal.
I have an old laptop I got and am trying to put on wmii but i don't know how to get it to start from the command line.

i like to have guis but dont have a good enough processor to be able to use a DE.

---

### Post by Lux Perpetua on 2008-04-30
Create a file in your home directory called **.xsession** with the contents ```
wmii
``` (or whatever the command line for the window manager is). After that, run the command **startx** and it should start the X server with wmii as the window manager.

**Edit:** actually, I'm not 100% sure that .xsession shouldn't be called .xinitrc instead. I think what I told you works, but you can cover your bases by making .xinitrc a symbolic link to .xsession.

---

### Post by olejorgen on 2008-04-30
I've read that you should do 
```
exec wmii
``` instead. Not sure why. You might need to make the file executable and include #!/bin/sh as well

---

### Post by chucky chuckaluck on 2008-04-30
*exec wmii* i .xinitrc is all i've ever needed. then, *startx* will take you to it.

---

### Post by Lostincyberspace on 2008-04-30
I know why it wouldn't work now I had not installed x so I took care of that.

---

