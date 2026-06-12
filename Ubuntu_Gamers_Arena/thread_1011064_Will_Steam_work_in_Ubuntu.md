---
title: "Will Steam work in Ubuntu?"
date: 2008-12-14
forum: Ubuntu Gamers Arena
---

### Post by Exit18 on 2008-12-14
I have Team Fortress 2 (and a number of other Source games) installed on my comp. Will I have to reinstall it, or make any changes? I'm pretty new to Linux-based operating systems, so excuse my lack of knowledge in this area. =(

---

### Post by donkyhotay on 2008-12-15
Need more information to answer this question. First of all what do you mean by "I have it already installed, do I need to reinstall it"? Is team fortress 2 installed on the windows partition of a dual boot computer, installed under windows of a ubuntu wubi installation, or installed on linux via wine already and having a problem and you want to know if a reinstall will fix it?

---

### Post by squeabs on 2008-12-15
I've seen numerous guides and such of people getting steam to work in wine with only small compatibility issues. It's in the [WineHq]("http://winehq.org") App Database.

[Steam on the WineHq App Database]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163")
It would be a safe bet to reinstall into the Wine virtual C:/ drive.

---

### Post by Exit18 on 2008-12-15
> **donkyhotay said:**
> Need more information to answer this question. First of all what do you mean by "I have it already installed, do I need to reinstall it"? Is team fortress 2 installed on the windows partition of a dual boot computer, installed under windows of a ubuntu wubi installation, or installed on linux via wine already and having a problem and you want to know if a reinstall will fix it?
What I meant was that I already had it installed on XP, but I'm starting to think it would be best to have a separate windows partition. Would that make things easier?

---

### Post by squeabs on 2008-12-15
It would be easier to have a separate windows partition.

---

### Post by donkyhotay on 2008-12-16
Although I've never tried it I would not recommend running a program from wine directly an already installed windows installation (even if it's a seperate windows partition). In order to be compatible with windows wine has it's own registry system just like windows does. Most programs create specific registry keys here during installation and won't work without them. Trying to run the program directly from the windows partition is like copying the program files from one windows computer to another and then trying to run it.

---

