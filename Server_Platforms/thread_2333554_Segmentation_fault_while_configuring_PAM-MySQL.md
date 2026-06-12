---
title: "Segmentation fault while configuring PAM-MySQL"
date: 2016-08-11
forum: Server Platforms
---

### Post by venirr on 2016-08-11
Hi, I'm new to this forum so I post my thread in 'New to Ubuntu' but my problem is a bit complicated...

I am trying to authenticate users against external mySQL database stored on a server. I do know that PAM can handle this and I found nice articles about it but each and every time during editing files I am stuck because of ```
segmentation fault, core dumped
``` I am not skilled in debugging such problems so I am not sure what is cause of this problem. I think that the sudo command has some issues because after segfault I can use Ubuntu in all manners (beside using sudo command - and shutting system down) and PC wont reboot (I still have acces to GRUB though). Memory test was fine and when I cared to not start any GUI apps through sudo and using gksudo instead problem still occured. 

Please, tell me what logs I should check in order to get to the bottom of this case. OS is Ubuntu Gnome 14.04

EDIT: this is the output of strace sudo command:
[http://textuploader.com/586qq](http://textuploader.com/586qq)

---

### Post by DuckHook on 2016-08-11
*Thread moved to **Server Platforms** as the more appropriate forum.*

---

