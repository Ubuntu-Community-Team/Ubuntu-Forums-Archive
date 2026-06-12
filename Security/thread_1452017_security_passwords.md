---
title: "security passwords"
date: 2010-04-11
forum: Security
---

### Post by alenn on 2010-04-11
how to disable all those security passwords which are anoying me every time I start something important for system.

sorry for bad english

---

### Post by aysiu on 2010-04-11
I have a better question: what are these important things you're starting that require root privileges?

There are probably either 1) ways to get those particular things to start up without a password or 2) better ways to implement what you want than the way you've been doing them.

No one is going to tell you how to disable password prompts altogether, or she'll get an infraction:
[Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by karthick87 on 2010-04-11
Startup passwords can be disabled by [COLOR="Red"]System>Administration>Login Window[/COLOR]

and select [COLOR="#000080"]Security Tab[/COLOR] and check [COLOR="Navy"]Enable Automatic Login[/COLOR]

Sudo password can be disabled by,

*Open Terminal

*type "[COLOR="#ff0000"]sudo visudo[/COLOR]" without quotes

*find the line that says [COLOR="#ff0000"]%admin ALL=(ALL) ALL[/COLOR] and change it to [COLOR="#ff0000"]%admin ALL=(ALL) NOPASSWD: ALL[/COLOR]

*Save and Exit,thats all..!

---

