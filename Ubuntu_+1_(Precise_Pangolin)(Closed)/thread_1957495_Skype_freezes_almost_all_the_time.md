---
title: "Skype freezes almost all the time"
date: 2012-04-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dcordeiro on 2012-04-12
Hi,

My Skype is freezing almost everytime I run it.

But the strange thing is that does not completely froze. I can right-click the icon, see the contacts list, open a new chat window (the messages are never delivered nor I can receive any message).

I'm just certain that Skype is frozen when I click quit. Then nothing happends and I must kill -9 it.


Any ideas of what may be happening?
I have this problem with different computers (with different hardwares, but both running the 64bit version of Ubuntu).


Thanks,
Daniel

---

### Post by na5h on 2012-04-12
The Linux version of Skype tends to have problems, I'm afraid. You could always try to download and install an older version of Skype...or you could use Skype through your web-browser using this awesome web-site: [imo.im]("https://imo.im/").

---

### Post by jadtech on 2012-04-12
one thing I noticed with Skype to is this make sure your software is up to date before you install Skype and make sure you update skype when you up date  the software it is defiantly touchy on Linux , about the same on some computer setups with window as well ..

---

### Post by dcordeiro on 2012-04-12
It seems that the problem is related to the 64bit version of Ubuntu (from 11.04):

There is a lot of messages on this thread at the Skype official forum:
[http://community.skype.com/t5/Linux/Skype-silently-crashes-on-Ubuntu/td-p/1162](http://community.skype.com/t5/Linux/Skype-silently-crashes-on-Ubuntu/td-p/1162)

But there is no official answer from Skype. :(

If Skype does not work correctly on Ubuntu 64bits, Canonical should stop distributing it or try to convince Skype to fix it.

---

### Post by dcordeiro on 2012-04-12
I filled a bug report (Bug #980320) but I don't have any hope that it will be fixed soon (I think it is out of hands from Ubuntu people).

If you are having the same problem, please mark this bug as affecting you.

---

### Post by cariboo on 2012-04-12
I'd suggest trying the Skype package from the Partner repository, I haven't had any problems with it.

---

### Post by dcordeiro on 2012-04-12
> **cariboo907 said:**
> I'd suggest trying the Skype package from the Partner repository, I haven't had any problems with it.

I'm using Skype from the partner repository. :(

---

### Post by alphacrucis2 on 2012-04-13
> **dcordeiro said:**
> I'm using Skype from the partner repository. :(

I also use the one from the partner repo. I have a somewhat different problem with it. It often goes into some sort of i/o loop just after starting up with the disk activity light stuck on solid. I can barely get into a terminal session to kill it. It seems to come right for a while if I delete the skype profile and let it recreate a new one but the problem eventually comes back. I never had any trouble with it under 11.04 but the issue started with 11.10 and is still with 12.04

---

### Post by treesurf on 2012-04-13
I am running the partner repository Skype with no freezes or other major problems.  However, it does refuse to follow the system theme.

EDIT: after latest compiz updates Skype is now following system theme.  My apologies for the useless post. :P

---

