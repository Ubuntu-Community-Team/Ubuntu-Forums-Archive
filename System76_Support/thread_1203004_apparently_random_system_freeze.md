---
title: "apparently random system freeze"
date: 2009-07-02
forum: System76 Support
---

### Post by Eli Dupree on 2009-07-02
Running Jaunty on a one-month-old System76 laptop (system model "daru3"). The system sometimes freezes when I'm not doing anything - the screen freezes and the computer doesn't react to keyboard or mouse input except force-shut-down with the power button. While it's frozen, the Caps Lock and Scroll Lock lights blink green.

A quick google search suggested that this might be a memory problem, but I ran memtest86+ and it passed.

What's going on? Is there anything I can do about this?

---

### Post by tessk on 2009-07-02
i have had the same problem half a dozen or more times. also on a 1-month old darter.

i haven't noticed the caps and scroll blinking, but i'll watch for that next time ... but fingers crossed there won't be many more next times :) it hasn't happened for at least 3 or 4 days.

i have always had firefox open when it happens, but then again i almost always have firefox open. other than that can't see a pattern.

---

### Post by philcamlin on 2009-07-02
try the fiirefox 3.5 beta :) see if that helps

---

### Post by elusivespoon on 2009-07-03
Sounds like this problem I had: [Computer Freezes, CapsLock and ScrollLock blink]("http://ubuntuforums.org/showthread.php?p=6262226#post6262226").
Installing linux-backports-modules-intrepid seemed to work for me. Hopefully linux-backports-modules-jaunty will do the same for you.

---

### Post by thomasaaron on 2009-07-03
Right, that is called a kernel panic. If you passed memtest, it's probably not hardware related.

Installing linux-backports-modules-jaunty might help. It's worked on some other machines. But if it doesn't, please do this...

IMMEDIATELY following the next kernel panic, shut your computer down, start it right back up and go straight to System > Admin > System76 Driver > Support > Create.

Attache the logs.tar file created in your home directory to this thread.

---

### Post by Cadeyrn on 2009-07-06
Also, it may not apply here because I'm not sure if my Pangolin or any other System 76 computer has a Broadcom wireless card, but a friend of mine as well as tons of other people with Broadcom wireless cards in Intrepid and Jaunty got that exact crash when their connection went below 40%. The simple fix is to uninstall GNOME's default wireless manager and install a new one.

---

### Post by tessk on 2009-07-06
It's only been a few days since I installed backports, but no more crashes so far!

---

### Post by Pronker on 2011-03-16
I have a problem that seems like it's the same in version 10.10. I suspect my wireless driver to be causing the trouble. I have an Atheros AR9285 card, which driver should I install instead?

---

### Post by isantop on 2011-03-17
What model of System76 Computer do you have? I'm not sure we've sold Atheros cards before.

---

