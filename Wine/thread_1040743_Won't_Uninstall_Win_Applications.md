---
title: "Won't Uninstall Win Applications"
date: 2009-01-15
forum: Wine
---

### Post by roystreet on 2009-01-15
Hello,
   I've been using WINE & it seems to work fairly well, although it sounds like crossover will work better.  Anyway, I've installed a dictionary program on my machine...It never would start.  Even though it seemed to install fine, even put the shortcut on my desktop!  Click on the icon, looks like it's going to run great!  Never starts.  OK, after that happening a few times I decided I would just uninstall the dictionary. I open up the "Uninstall Wine Software" & list lists all of the windows apps installed by Wine.  I click on the dictionary app & then click uninstall.  Nothing ever happens.  I've done it many times, nothing happens.  I look to see what's running by opening the system monitor.  I see a wine uninstaller app running (At least that's what it appears to be)  I wait...Nothing ever happens.  I end up killing the process.

Any ideas of why this is happening?
Thanks,
~roystreet

---

### Post by EnderEcho on 2009-01-15
Whatever was preventing the program from running might be preventing it from uninstalling. You may have to resort to manually deleting everything from the C: drive. When you do that you have to manually delete the shells that make those programs show up in the wine menu.

---

### Post by roystreet on 2009-01-16
Question for you...Where are the shell files located that you are referencing?  I did go into the C drive & delete anything that I could tell had to do with the application, but I do still see the name of the app still in the menu like you said.

Thanks!
~roystreet

---

