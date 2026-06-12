---
title: "Hamachi Install failure"
date: 2011-10-14
forum: Server Platforms
---

### Post by LordJebe on 2011-10-14
So, I am trying to install Hamachi on my 10.04 LTS server machine according to [this]("http://dougmelton.com/other-fun-stuff/hamachiubuntuhowto/") tutorial. Every time I try to install Hamachi, it just gives me this error:
 
sudo make install
Copying hamachi into /usr/bin ..
Creating hamachi-init symlink ..
Copying tuncfg into /sbin ..
install: cannot run strip: No such file or directory
install: strip process terminated abnormally
make: *** [install] Error 1&#65279;

I have no idea what is causing the problem.

---

### Post by LordJebe on 2011-10-15
Bumping, could someone please help me with this problem? :(

---

### Post by LordJebe on 2011-10-24
Well, I found out myself that the problem was that I hadn't installed GCC. I installed it, and ran into another problem. As I try to start Hamachi, I run into this error:
```
sudo hamachi -c /etc/hamachi start
24 23:45:08.078 [   0] [ 6204] tap: connect() failed 2 (No such file or directory)
```

Someone please help, I've been trying to get this thing to work for a week now with no results...

---

### Post by LordJebe on 2011-10-26
Ah, the problem was that I hadn't ran sudo /sbin/tuncfg. Thank you all for help ;)

---

