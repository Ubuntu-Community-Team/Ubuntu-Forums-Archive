---
title: "Filter Synched Files"
date: 2010-06-09
forum: Ubuntu One (CLOSED)
---

### Post by HornedBeast on 2010-06-09
Hi.

Is there anyway to change which files get synced over Ubuntu One? I imagine all the usual temp files and things are simply ignored when syncing a folder - but I was wondering if there was any way to set some parameters?

Such as, ignore ".iso", ".mp3", that kinda thing... or explicitly say, only sync ".doc" in this folder?

I'm not expecting a GUI tool to be able to do this (yet), but a point at the right piece of Python or something similar could be handy :).

**Update: **

I found this under : /etc/xdg/ubuntuone/syncdaemon.conf

Simply append and mend:

```
ignore.default = \A#.*\Z
                 \A.*~\Z
                 \A.*\.py[oc]\Z
                 \A.*\.sw[nop]\Z
                 \A.*\.swpx\Z
                 \A\..*\.tmp\Z
```

With whatever you want. You can add .iso, for example, by doing this...


```
ignore.default = \A#.*\Z
                 ........---.........
                 \A\..*\.tmp\Z
                 **\A.*\.iso\Z**
```

Hope that helps someone out!.


Cheers,

Andy

---

### Post by laoshi on 2010-06-12
Do you have any idea whether this could work also, if written into ~/.config/ubuntuone/syncdaemon.conf - in order not to tamper with files in /etc/ ?

---

### Post by Thezealite on 2011-05-26
Any follow-up on whether this can be done through ~/.config/ubuntuone/syncdaemon.conf ?

---

### Post by duanedesign on 2011-05-31
Yes, it will work, it will be called "ignore" in [__main__] section of ~/.config/ubuntuone/syncdaemon.conf

---

