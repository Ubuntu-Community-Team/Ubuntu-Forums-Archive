---
title: "Module 'ffmpeg' already loaded in Unknown on line 0"
date: 2009-07-02
forum: Server Platforms
---

### Post by wattaman on 2009-07-02
Long story short: what does this mean:
> [19-Jun-2009 16:24:24] PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/ffmpeg.so' - /usr/lib/php5/20060613+lfs/ffmpeg.so: cannot open shared object file: No such file or directory in Unknown on line 0
[19-Jun-2009 16:25:30] PHP Warning:  Module 'ffmpeg' already loaded in Unknown on line 0
and how do I fix it (if I should)?
Thank you!

---

### Post by credobyte on 2009-07-02
What about .. removing current version and reinstalling ?
```

sudo apt-get remove --purge php5-ffmpeg && sudo apt-get install php5-ffmpeg && sudo /etc/init.d/apache2 restart
```

---

### Post by wattaman on 2009-07-03
Didn't worked... you see, I'm trying to make it work with the OsDate script, but doesn't want to convert the uploaded videos. Does ffmpeg keepserror logs somewhere? maybe I'll find a tip there.

---

### Post by wattaman on 2010-04-15
Still getting this error in the php error logs.
Any idea how to fix the "PHP Warning:  Module 'ffmpeg' already loaded in Unknown on line 0"

---

