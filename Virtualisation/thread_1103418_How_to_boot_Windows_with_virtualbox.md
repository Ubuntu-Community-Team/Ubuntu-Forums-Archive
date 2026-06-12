---
title: "How to boot Windows with virtualbox"
date: 2009-03-22
forum: Virtualisation
---

### Post by superalanliu on 2009-03-22
I have an existing installation of windows which I dual boot off of. Is there some way I can just access it using virtualbox?

---

### Post by bodhi.zazen on 2009-03-23
EDIT: OK, I jailed the two posts with misinformation.

Also I retitled your thread.

/end edit

========


Neither of those replies are accurate. Please if you do not know, do not give out flase information.

You can boot physical partitions with VirtualBox , but be warned that this is in Beta nad if you make a mistake you can cause massive data loss.

Windows doe snot like this as when you boot it with Virtualbox it will detect that the hardware has changed. You will have some limitations in that Virtualbox does not directly access your videocard for example.

FYI: You really should check out the sticky, it is a sticky for a reason ;)

[http://ubuntuforums.org/showpost.php?p=6122463&postcount=6](http://ubuntuforums.org/showpost.php?p=6122463&postcount=6)

Here are the two threads for how to boot windows with virtualbox :

[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

---

### Post by odinb on 2009-03-23
> **superalanliu said:**
> I have an existing installation of windows which I dual boot off of. Is there some way I can just access it using virtualbox?

Could this be useful?

[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)

---

