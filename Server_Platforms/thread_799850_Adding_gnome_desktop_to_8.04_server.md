---
title: "Adding gnome desktop to 8.04 server"
date: 2008-05-19
forum: Server Platforms
---

### Post by markdjones82 on 2008-05-19
All, I installed gdm, gnome-core, firefox etc using apt-get.  Yet, when I reboot I do not get any desktop coming up.  I cannot start a gnome-session either.  Any help on what I may be doing wrong?

Edit: startx gives me this error:

x cannot start /etc/X11/X no such file or directory

---

### Post by solcott on 2008-05-19
sudo apt-get install gnome-desktop-environment

I added GNOME to my server for hosting Windows game server software on Wine and couldn't start the X server at first until I saw the gnome-desktop-environment metapackage that fixed my problems :-)

---

### Post by ginjabunny on 2008-05-19
try - sudo apt-get install xorg gdm gnome-core - this gives you a really basic gnome then you can add more later

do not do - ubuntu-desktop - or you will get everything

---

### Post by markdjones82 on 2008-05-19
Thanks, I figured it out.  I didn't install the xorg portion of it hehe.

Also, if anyone is looking to change the login screen background.  It had this really lame flower.  Use gdmsetup

---

