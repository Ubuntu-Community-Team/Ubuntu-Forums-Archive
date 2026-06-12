---
title: "dependency hell !"
date: 2007-09-23
forum: Server Platforms
---

### Post by neill on 2007-09-23
hi

i want to install bitdefender on my headless server (i ssh in from my desktop)

this needs libstdc++5 and sudo apt-get install libstdc++5 produces a dependancy for gcc-3.3-base

but apt-get install gcc-3.3-base gives a dependency for libstdc++5 !!

how do i break the circle ??

---

### Post by z0mbie on 2007-09-23
Use **sudo aptitude install **instead of sudo apt-get install. Also make sure you have all the repositories in your **/etc/apt/source.list**. 
Check out:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Manually_edit_sources.list](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Manually_edit_sources.list)

---

### Post by neill on 2007-09-23
that worked fine - thanks

ps

awesome avatar !!!

---

