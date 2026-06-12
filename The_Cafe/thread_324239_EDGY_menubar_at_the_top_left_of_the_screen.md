---
title: "EDGY: menubar at the top left of the screen?"
date: 2006-12-23
forum: The Cafe
---

### Post by moon_dog on 2006-12-23
i just did a clean install of EDGY and i noticed that with certain apps (command terminal, rythmbox, etc) the menubar appears at the top left of the screen, completely detached from the application window.  is there any way  to get rid of that?

---

### Post by MetalMusicAddict on 2006-12-23
Odd. Could you post a screenshot?

---

### Post by Kimm on 2006-12-23
sounds like a GTK problem to me...

try:

sudo apt-get --reinstall install libgtk2.0-0

---

### Post by aidanr on 2006-12-23
did you try to install the mac menu bar by any chance?
 [http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868)

---

### Post by moon_dog on 2006-12-23
yep, i tried to install the macmenu bar but it didn't work.   so it's a related problem?  here's the screenshot

---

### Post by aidanr on 2006-12-23
yup, try reinstalling libgtk2.0 through synaptic and remove the mac menu applet from the panel

---

### Post by moon_dog on 2006-12-24
cool that worked thanks.

---

