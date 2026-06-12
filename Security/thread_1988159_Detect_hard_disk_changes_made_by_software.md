---
title: "Detect hard disk changes made by software"
date: 2012-05-27
forum: Security
---

### Post by vikkyhacks on 2012-05-27
Is there any software that can detect what changes the software is making on my disk ...
Suppose I browse with firefox then it updates cache and all kinds of network stuff on my harddisk, Is there any any waw to find where and what changes are made by there softwares ...????

---

### Post by unspawn on 2012-05-27
> **vikkyhacks said:**
> Is there any software that can detect what changes the software is making on my disk ...
There's different ways depending on what your scope is and what you want to get out of it like: 
- the "audit" service ([example](http://www.cyberciti.biz/tips/linux-audit-files-to-see-who-made-changes-to-a-file.html)),
- a file system integrity monitor like Samhain (see "5.4.13. Who made changes to a file?" [here](http://www.la-samhna.de/samhain/manual/filedef.html)),
- inotify (see [this](http://www.linuxjournal.com/article/8478), [this](http://www.ibm.com/developerworks/linux/library/l-inotify/index.html?ca=drs-) or [this](http://www.cyberciti.biz/faq/linux-inotify-examples-to-replicate-directories/)) or 
- verifying hashes with say *md5deep*.

---

### Post by vikkyhacks on 2012-05-28
Thanks for the reply.... but i need not monitor any changes made in a directory/file ...
Think of ollyDBG, when i run any software inside it, it will display all the changes made into the processor's registers, stack and all other access made by the program...
  Likewise the software that i am imagining right now will have to run inside and monitoring software and when i hit play it should display all the directories and files accessed by it....

---

### Post by unspawn on 2012-05-28
*shrug* like I said it depends on what you want to get out of it. It's not like your distros repo, Freshmeat, Sourceforge, Savannah or Berlioz show Linux lacks debuggers...

---

