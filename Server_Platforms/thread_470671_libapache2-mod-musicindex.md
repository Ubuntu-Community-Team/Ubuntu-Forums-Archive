---
title: "libapache2-mod-musicindex"
date: 2007-06-11
forum: Server Platforms
---

### Post by mzracer360 on 2007-06-11
I am wanting to know if **libapache2-mod-musicindex** still works with Ubuntu.  I had it on my Ubutu 6.10 server, but now that Im using 7.04, I can't get it to work.  I get this error when I try to start/restart Apache:

```
Invalid command 'MusicCssDefault', perhaps misspelled or defined by a module not
 included in the server configuration                                                                  [fail]
```

---

### Post by EndPerform on 2007-06-11
Judging by that error message, it doesn't appear to be installed.  Did you upgrade or install 7.04 from scratch?

---

### Post by mzracer360 on 2007-06-12
I installed from scratch.  From my experience with Ubuntu, when I upgrade, it tends to ruin my apache setup:-(

BTW, I used this [How-To]("http://ubuntuforums.org/showpost.php?p=1832320&postcount=6") which worked fine on 6.10.

---

### Post by ubu_dynamite on 2007-08-27
change:
MusicCssDefault     musicindex.css
MusicCachePath      /tmp/musicindex

to:
MusicDefaultCss     musicindex.css
MusicIndexCache    /tmp/musicindex

names changed this workt for me

---

