---
title: "please help me"
date: 2007-01-13
forum: Ubuntu System Panel
---

### Post by Bossieman on 2007-01-13
Okey, i have been trying to get plugins to work and I have had no luck at all. Im supposed according to a thread here to put the plugin-files in the ~/.usp/plugins folder. 
In that folder i Have:

calculator.glade  internet.py   template.glade     uspcalendar.py
calculator.py     notes.glade   template.py        usptime.glade
calrem.glade      notes.py      terminal.glade     usptime.py
calrem.py         remind.glade  terminal.py
internet.glade    remind.py     uspcalendar.glade

But none of the above is avaliable in the menu.

---

### Post by Malac on 2007-01-13
Have you added them to your plugins list
either using gconf-editor key /apps/usp/plugins_list
or using preferences from the right-click menu (if you are running 1.9x alpha test)

Hope this helps.

---

### Post by Bossieman on 2007-01-13
I think I just give up. I dont get it. In USP config  I hit add and put in "terminal", nothing happens after save and refresh. 
I will try to completely remove everything and then reinstall it.

EDIT: After the reinstall everything worked!

---

