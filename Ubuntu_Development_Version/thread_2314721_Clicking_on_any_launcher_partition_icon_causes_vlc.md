---
title: "Clicking on any launcher partition icon causes vlc start"
date: 2016-02-23
forum: Ubuntu Development Version
---

### Post by van hanegen on 2016-02-23
Ubuntu 16.04, upgrade from 15.10 (with this bug already existed).
VLC 3.0 or 2.2.1 - doesn't matter. Of course the problem can be solved by removing VLC.
But can you find another solution?
P.S. Never had such an issue with my main 14.04 install.
[URL="https://youtu.be/Ld7Mzxv8pD0"]be/Ld7Mzxv8pD0


[/URL]

---

### Post by howefield on 2016-02-23
Moved to the "*Ubuntu Development Version*" forum.

Have a look for anything odd in System Settings > Details >  Removable Media

---

### Post by van hanegen on 2016-02-23
I can't see anything strange there. VLC never even mentioned.

---

### Post by mc4man on 2016-02-23
Take a look in or post the contents of ~/.local/share/applications/mimeapps.list

---

### Post by van hanegen on 2016-02-23
[Default Applications]
inode/directory=nemo.desktop
application/x-gnome-saved-search=nemo.desktop

---

### Post by mc4man on 2016-02-23
i'd set up a new user in system settings > user accounts, log into that user & see what happens there. If all is ok then it's some local config to your user.
Why are you using nemo.desktop in an ubuntu session?

---

### Post by van hanegen on 2016-02-23
It's ok with a new user!:o
So, where  can i find that wrong local config then?

P.S. I'm using nemo, 'cause the lack of some important features in default nau, eg "Open with..." in folder context menu

---

### Post by dino99 on 2016-02-23
you might purge (complete removal, not a simple uninstall) vlc then reinstall it

> sudo apt-get purge vlc*

---

### Post by van hanegen on 2016-02-23
Deleted minesapp file in the .config folder and that's it!!!
**mc4man**, thank you very very much!

---

### Post by mc4man on 2016-02-23
The open with on folders was returned to nautilus, it should be available in the current one that 16.04 is using, screen

---

### Post by van hanegen on 2016-02-23
Yeah, that's true.
Many thanks!

---

### Post by mc4man on 2016-02-23
I'll probably have 1 modified nautilus for 16.04 (vs. on trusty where there were so many that broke into separate ppa's) in [this ppa]("https://launchpad.net/~mc3man/+archive/ubuntu/nauty-hacks1")
Currently using here - 
revert-canvas-view-hover1.patch  # no opening of folder when hovering in canvas view, hover open folder in sidebar was removed, hover open remains on breadcrumbs
date-time-full.patch  # option in *list view* for full date-time timestamp thru the "Modified (full)" column
name.patch # Icon in launcher is more apppropiate of 'File Manager'
tool1.patch # adds a parent button to toolbar
pkexec2.patch # adds built-in pkexec policy & command 
details1.patch  # adds a new list view column "Type (detailed)" to give detailed mime info
expand_filename_on_hover.patch # returns getting full file name on hover vs. current of only on click
no_me2.patch # use actual user name instead of 'me'

---

### Post by QDR06VV9 on 2016-02-23
I have seen something similar with Mate on xenial, but instead of the file manager being opened by VLC it was audacious.
Simple fix though with system settings and prefered application's  File's open with "Caja"    
Going to use Doug's PPA for trusty && nautilus..
As I too was using Nemo for a better work flow.
Regards

---

### Post by mc4man on 2016-02-23
> **runrickus said:**
> I have seen something similar with Mate on xenial, but instead of the file manager being opened by VLC it was audacious.
Simple fix though with system settings and prefered application's  File's open with "Caja"    
Going to use Doug's PPA for trusty && nautilus..
As I too was using Nemo for a better work flow.
Regards
If you end up using any of those builds,  for root nautilus, (command is pkexec nautilus) it's preferable to not run the command thru a terminal. 
Better to use a run dialog, in an ubuntu session Alt+F2 (unity saves run commands so will be shown in subsequent Alt+F2's

---

### Post by QDR06VV9 on 2016-02-23
Understood! And thanks for the heads up!:D

---

