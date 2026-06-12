---
title: "Have all subdir/subfiles have permissions?"
date: 2011-11-19
forum: Server Platforms
---

### Post by justinram22 on 2011-11-19
Hello!

Basically I'm trying to setup a webserver and am running to this problem.  /var/www/ is non-write permissions which I know can easily be fixed by (and all sub directories) chmod 777 -R

But this only works for all current files and dirs... Is there a way to make it permanent for all future files?

Thanks guys!  Basically I have a script that creates a new dir in /var/www/ and chmod 777's it, but then any file I create inside that dir still has non-write permissions?

---

