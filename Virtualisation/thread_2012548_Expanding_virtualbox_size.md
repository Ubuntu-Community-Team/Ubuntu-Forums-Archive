---
title: "Expanding virtualbox size"
date: 2012-06-29
forum: Virtualisation
---

### Post by wbrokow1 on 2012-06-29
I have installed virtualbox 4.something with win xp on it.
Installation size is 10gb. I am trying to install a program on xp
and it's telling me I need more room to install the program.
I tried the manager with --resize option but I got an error telling me I wasn't allowed to do that.  I am using 11.10 ubuntu.
Any suggestions on fixing this?
Thanks for any help.

---

### Post by wbrokow1 on 2012-07-02
Anyone?

---

### Post by Habitual on 2012-07-02
```
VBoxManage modifyhd YOUR_HARD_DISK.vdi --resize SIZE_IN_MB
```
says [http://www.webupd8.org/2011/02/how-to-easily-resize-virtualbox-40-hard.html](http://www.webupd8.org/2011/02/how-to-easily-resize-virtualbox-40-hard.html)

HTH

---

### Post by wbrokow1 on 2012-07-06
had to use a partition resizer called Ease...something.
available for free on cnet downloads.
Worked ggreat.

---

### Post by howefield on 2012-07-07
Thread moved to the "*Virtualization*" forum.

---

### Post by wildmanne39 on 2012-07-07
Hi, if you create your next guest with dynamic expanding disk then it will grow as you install new applications.
Thanks

---

