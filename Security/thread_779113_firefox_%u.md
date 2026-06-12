---
title: "firefox %u"
date: 2008-05-02
forum: Security
---

### Post by SICCpenguin on 2008-05-02
I have searched endlessly and cannot find a solution to my my problem, although there are many solutions for similiar problems. Whenever I log on, firefox loads automaticaly with the address %u which says cannot be displayed. My homepage is set to google. I changed all references in the launchers from "firefox %u" to "firefox, as well as changing any similiar references in gconf-editor. I uninstalled firefox, wiped profiles and even erased the .mozilla for both guest and root, reinstalled, and still the same thing, every single log in.

I thought the problem was associated with cairo-dock, but wiped that out and repeated above procedure and still nothing. There was a picture i downloaded one time to my desktop that still makes me curious, the pic downloaded and then just diappeared from the desktop. Think its related?? I found 2 hidden files on desktop, .commands and .sources, and removed them both, but still nothing.

Does anyone know a solution to this or have similar problems?

P.S... Im a newb at the forums, think i put this in the wrong category....

---

### Post by SICCpenguin on 2008-05-04
I found the solution, i removed firefox from the .config/autostart in the home directory(took some searching), but finally found it! Had 2 look at the hidden files. Still dont know how it was caused though, sen nothing else online for similiar problems.

Also, the problem is related to cairo-dock, when trying to move a luancher, if you accidentally drag the launcher into another icon(which is easily done), then that program will try to execute the launcher.  This obviously causes some serious confusion, which unfortunatly sticks around even after rebooting. I still need to figue out how to clear the rest of the launchers i messed up for cairo-dock, even after wiping the profiles and reinstalling it. At this point brasero tries to load %u also when application starts, and GIMP complains about something i cant remember when starting up.

---

