---
title: "Persistent problem with ATI Catalyst"
date: 2012-03-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Xgen on 2012-03-26
For quite a while now, the Catalyst settings don't persist after a reboot and the screen becomes extremely light. To correct the problem, I need to toggle any setting in the Catalyst Center and exit. At one time, I added 'xgamma -gamma (.xxx) to the Startup Applications menu, but that doesn't work now. Anyone else with this problem, and possibly a solution? Works fine in Oneiric and Natty.

---

### Post by scaine on 2012-03-26
Yep, Samsung Chronos 7 here, with ATI 5760M and the brightness is reset to full brightness on every reboot and even a resume from suspend. Screen blanking works okay and preserves brightness.

If I go to the brightness settings on reboot, I find that it *thinks* the brightness is low, but it's (obviously) not. Touching the slider immediately jumps the brightness to the lower setting and works fine.

I haven't gotten round to logging a bug, as I find it's often counter-productive to log hardware-specific bugs during a beta. I'll wait until late April and if it's still happening, I'll do it then.

---

### Post by Xgen on 2012-03-28
Okay... found that 'xgamma -gamma .650' now works in terminal and even if I map a mouse button combination to the command. It will not work in Startup Applications or in any home bash files or as a standalone script in /etc/init.d. How else can I get this command to work on startup?

Nevermind - found that it will now work it I add 'sleep 2' to the command in the Startup Applications menu...obviously needs a delay now. Will mark as 'Solved'.

---

