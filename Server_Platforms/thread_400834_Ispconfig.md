---
title: "Ispconfig"
date: 2007-04-04
forum: Server Platforms
---

### Post by M0rThden on 2007-04-04
I dont know if anyone uses ispconfig, but i just recently installed it. It seems to be working alright, although i dont know how to use it.

If there are any good guides out there that explain it let me know because i cant find them.

Its giving me an error when i try and install the new version of phpmyadmin. 

So any help would be great. All im trying to do is host my own website and mabey a few others.

Thanks!

---

### Post by huygens on 2007-04-04
I have read that ispconfig has some trouble with the default sh script.
In few words:
ispconfig is a shell script that using shell extension provided by bash (one of the existing shell script engine)
Ubuntu uses dash (another shell script engine) for the default sh engine. Dash does not have the specific extension of bash.
Impact, ispconfig has some bug when using it under Ubuntu.

Solution, make ispconfig using bash.

How: edit ispconfig with a text editor (you probably will need to have super user privilege by using sudo or gksudo). The first line of this script should be something like "#!/bin/sh" replace it by "#!/bin/bash". Save the file and try it again.

---

### Post by Aberrix on 2007-04-04
> **M0rThden said:**
> If there are any good guides out there that explain it let me know because i cant find them.

[http://www.howtoforge.com/forums/forumdisplay.php?f=14](http://www.howtoforge.com/forums/forumdisplay.php?f=14)

The ISPConfig forums (link above) have been indispensable to me, people there know it inside and out, the creators are on the forums and I've generally gotten a response/solution to a post within 3 hours at most.

I've been using ISPConfig for roughly 4 months and have zero complaints.

gl mate.

---

### Post by M0rThden on 2007-04-04
> **huygens said:**
> 
How: edit ispconfig with a text editor (you probably will need to have super user privilege by using sudo or gksudo). The first line of this script should be something like "#!/bin/sh" replace it by "#!/bin/bash". Save the file and try it again.

The perfect setup guide has you change it by doing this. 

```
rm -f /bin/sh
ln -s /bin/bash /bin/sh
```

it didnt help.

And ive already posted in their fourms with no luck so far.

---

### Post by M0rThden on 2007-04-04
could i install phpmyadmin not through ISPConfig

---

### Post by M0rThden on 2007-04-06
I dont think it was the bin/bash problem. Im running it now on debian 1.3.1 and it still wont install the .pkg file. It still gives me the same problem

---

