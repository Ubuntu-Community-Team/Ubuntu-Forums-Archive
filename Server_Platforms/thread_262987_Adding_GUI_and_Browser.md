---
title: "Adding GUI and Browser?"
date: 2006-09-22
forum: Server Platforms
---

### Post by shultzjr on 2006-09-22
I understand that the server install does not include a gui.  I would like to install gnome/firefox for browsing and research but I do not want the server to boot into a gui mode on startup.  So my question is what apt-get commands do I need to run so I can fire up gnome/firefox when I type in the "startx" command?

thanks,
charles.....

---

### Post by tuxthepenguin on 2006-09-25
apt-get install gnome (For Gnome Desktop)
apt-get install kde (For KDE Desktop)

---

### Post by skymt on 2006-09-25
When you run startx, it runs a script at "~/.xinitrc". Put a script there that runs "gnome-session". Then, in GNOME, go to System > Preferences > Sessions and add firefox as a startup item.

---

