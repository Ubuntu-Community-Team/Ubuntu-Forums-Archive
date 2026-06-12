---
title: "Administrator is immediately logged off"
date: 2013-09-17
forum: Ubuntu Development Version
---

### Post by qwerty3656 on 2013-09-17
I have had a basic ubuntu 12.04 server for about a year (headless system, control through webmin, mobaxterm, and filezilla).  I recently upgraded to 13.1, which went fine.  I then installed virtualbox (and created a virtualbox user) which also seemed to go fine, but soon after that, my system became inaccessable.  I hooked up a keyboard and monitor and tried to log in at the server box.  It seems to log in fine, but then immediately logs me back off (w/o any error) and shows the log-in screen again.  If I log in with a non-admin user, I can log in fine (but have limited superuser control).  I've searched for a solution, but I'm at a loss.

---

### Post by buzzingrobot on 2013-09-17
Is "13.1" 13.10 or 13.04?

If the former, that's not released yet, so there could be all kinds of explanations for your problem.  Questions about 13.10 should go to the "Ubuntu+1" section here.

---

### Post by qwerty3656 on 2013-09-17
It is 13.10.

---

### Post by qwerty3656 on 2013-09-17
I have had a basic ubuntu 12.04 server for about a year (headless  system, control through webmin, mobaxterm, and filezilla).  I recently  upgraded to 13.10, which went fine.  I then installed virtualbox (and  created a virtualbox user) which also seemed to go fine, but soon after  that, my system became inaccessable.  I hooked up a keyboard and monitor  and tried to log in at the server box.  It seems to log in fine, but  then immediately logs me back off (w/o any error) and shows the log-in  screen again.  If I log in with a non-admin user, I can log in fine (but  have limited superuser control).  I've searched for a solution, but I'm  at a loss.

---

### Post by cariboo on 2013-09-17
I don't suppose there is any way you can check /var/log/auth.log, to see what is happening.

---

### Post by QIII on 2013-09-18
Threads merged.

---

### Post by steeldriver on 2013-09-18
I wonder if something got screwed up in your primary account's startup scripts (.profile / .bashrc etc.)? if so, and the ssh server is still starting OK, you could try ssh'ing in with a noprofile shell

```
ssh  *yourserver* bash --noprofile --norc
```

(be aware you won't even get a shell prompt!). Similarly, you could try logging in as a non-admin user and then su'ing with something other than your regular shell (and without the '-l' or '--' login shell option) e.g.

```
su -s /bin/sh *adminuser*
```

If neither of those work, then I think you will need to boot into recovery mode and go in via the root shell.

---

