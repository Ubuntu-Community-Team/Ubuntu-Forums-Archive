---
title: "-=Startup Script Help=-"
date: 2007-02-27
forum: Ubuntu Christian Edition
---

### Post by runkidrun on 2007-02-27
I play just 1 game on Ubuntu CE and that game is Wolfenstein: Enemy Territory...I also attempt to use TeamSpeak during my games...But, when I go in-game I can only hear TeamSpeak..(No In-Game Sound)...

So, I found a piece of code that will fix the problem:


```
echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss
```

**How would I make that code be included in the startup script?????????** (So It Works Everytime I Log In)

Thanks In Advance!

---

### Post by apakun on 2007-03-03
Try this: [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by dark_religion on 2009-11-13
Try reading here:
[http://ubuntuforums.org/showthread.php?t=66733](http://ubuntuforums.org/showthread.php?t=66733)

---

### Post by aysiu on 2009-11-13
This thread is two and a half years old. Why revive it?

---

