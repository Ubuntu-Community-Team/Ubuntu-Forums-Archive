---
title: "rungetty autologin"
date: 2011-02-14
forum: Security
---

### Post by sonofaforester on 2011-02-14
So I've got Ubuntu Command Prompt Only version 10.10 running on a PC-104 computer in a "headless" environment with no monitor or keyboard.  I installed rungetty and in the tty1.conf file have the command:

exec /sbin/rungetty tty1 --autologin username

This will work great, logging the user in automatically for a while, then suddenly stop working and I can't ever get it to work again, it simply prompts me for a login as if the --autologin switch wasn't there. 

1. Is there a rungetty log or something to help me diagnose the problem?
2. Is there a more appropriate way to automatically log a user in?

Thanks,
Mark

---

