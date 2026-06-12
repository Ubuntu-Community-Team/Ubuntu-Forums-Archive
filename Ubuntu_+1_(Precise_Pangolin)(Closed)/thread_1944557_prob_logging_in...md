---
title: "prob logging in.."
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-03-21
Whenever I try to login to my user, all I get is the background pic and nothing else - no desktop/unity. I can bring up a virtual terminal (ctrl + alt + F1), and when I press on the PC power button I get the option of suspend/restart/cancel/shutdown.

If I log into my wife's account, everything works OK (I'm writing this from there now).

Any help to sort this without a re-install would be much appreciated!

Cheers.

---

### Post by alphacrucis2 on 2012-03-21
Try Ctrl alt f1 then log in to terminal session using the account that doesn't work via the GUI. Then try 

```
unity --reset
``` 

Log Gui out of wifes account then back in as the account that was broken. May or may not help.

---

