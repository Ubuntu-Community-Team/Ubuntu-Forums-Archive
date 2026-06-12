---
title: "Ubuntu Virtual Machine can't mount directories"
date: 2015-03-17
forum: Virtualisation
---

### Post by christopher888 on 2015-03-17
The virtual machine is running on CentOS5 - virtual host manager
Please advice on how to fix Virtual Machine...

[ATTACH=CONFIG]260688[/ATTACH]

[COLOR=#333333][FONT=Helvetica Neue]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue] I already read about using a live-cd and start a file system check, but how can i do that ?

Many thanks in advance!


[COLOR=#777777]
[/COLOR]


[/FONT][/COLOR]

---

### Post by SeijiSensei on 2015-03-17
That VM has serious problems.  The code at the top of the image indicates a kernel exception which may, or may not, explain why it cannot find /sbin/init.  Try reinstalling to a new VM and see if that works better.

---

