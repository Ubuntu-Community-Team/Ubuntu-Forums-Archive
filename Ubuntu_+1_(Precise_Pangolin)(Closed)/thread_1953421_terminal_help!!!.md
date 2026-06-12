---
title: "terminal help!!!"
date: 2012-04-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by AnojiRox on 2012-04-06
Help!!

Ever since having upgraded to 12.04; terminal tels me this when I put the wrong command in:

```
anojirox@D4rkPh30n1X:~$ wrongcommand
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 17, in <module>
    from CommandNotFound.util import crash_guard
ImportError: No module named CommandNotFound.util
```Bit of help???

P.S.: all commands seem to be working...

---

### Post by dino99 on 2012-04-06
log out/in or reboot

---

### Post by AnojiRox on 2012-04-06
woops, my fault! I stupidly changed the default python from 2.7 to 3.2. that _might_ have something to do with it...

---

