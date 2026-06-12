---
title: "[SOLVED] How to install SSH Server?"
date: 2008-01-14
forum: Server Platforms
---

### Post by mdigitale on 2008-01-14
Hello friends,

  I want to install an SSH daemon so I can remotely connect to my Ubuntu Linux 6.06 LTS box.  Searching Google has led me to believe that it *should be* as easy as typing:

sudo apt-get install openssh-server

However, when I issue the above command I get:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package openssh-server

I've found others who have received the same error, but have not read of any solutions.  I have all the repositories selected in package manager (when I search for openssh via the GUI manager it only finds openssh-client, which is installed)


Help!!! :]

Mike

---

### Post by dgray_from_dc on 2008-01-14
Enable universe and multiverse in your repositories. Then retry.  That's all I've needed to do in the past.

---

### Post by kvonb on 2008-01-14
-

---

### Post by metoor30 on 2008-01-14
Try just 'sudo apt-get install ssh', usually works for me.  You can always run a 'sudo aptitude search ssh' to find the packages that are available to install with the word ssh in the name.

---

### Post by mdigitale on 2008-01-14
Updating did the trick -- thanks kvonb!

---

