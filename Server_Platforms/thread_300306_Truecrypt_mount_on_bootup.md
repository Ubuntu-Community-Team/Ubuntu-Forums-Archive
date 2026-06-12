---
title: "Truecrypt mount on bootup?"
date: 2006-11-15
forum: Server Platforms
---

### Post by shade73 on 2006-11-15
Ok so I have truecrypt running great.  However, I want to make the file I created my home directory.  To do this I'm trying to make it ask me for my passwd to mount the file on bootup.  So when it's scrolling the bar of ubuntu  at bootup i want it to break out of the screen and ask me for the passwd to mount my volume.  If it doesn't successfully mount then when I try to log in with my user there will be no home directory (or it will be empty).  I've tried adding a small script called tc in my init.d and linking it in rcS.d.  Here's the text of the script (names changed for obvious reasons).

#!/bin/bash
truecrypt /home/myName/myfile /home/myname/mymount -u


now it works fine when i run the script here, but on bootup it either skips it or fails (not sure which cuz i can't see it and it doesn't break out of the ubuntu logo).

any suggestions would be appreciated!

---

