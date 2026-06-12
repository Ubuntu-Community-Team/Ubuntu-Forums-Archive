---
title: "Startup Applications"
date: 2013-05-19
forum: Ubuntu Development Version
---

### Post by cecilpierce on 2013-05-19
Is something wrong with Startup Applications ? When I add "Login Sound" and save it and reboot its not there anymore ???...:(

---

### Post by kuvanito on 2013-05-19
that's weird,I just did it and it's there:

Dash/Applications/Startup Applications
Click on Add
Name:Startup Sound
Command:/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login sound"
Click od Add and Close
Reboot PC

---

### Post by 2F4U on 2013-05-19
Is it set to be visible? Check if the .desktop file has NoDisplay=true in it since then the application is not visible. If yes, change it to NoDisplay=false.

---

### Post by cecilpierce on 2013-05-19
Thanks, working now. I don't have a .desktop file in my user dir ?

---

