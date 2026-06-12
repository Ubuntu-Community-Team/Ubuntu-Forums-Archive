---
title: "Comand line problem"
date: 2006-04-16
forum: Server Platforms
---

### Post by awillcott on 2006-04-16
I did a successful install of ubuntu, but i get a comand line after entering user name and password, what to enter here? please help.:???:

---

### Post by IYY on 2006-04-16
Try

sudo dpkg-reconfigure xserver-xorg

---

### Post by nanotube on 2006-04-16
IYY gives good suggestion

your getting a non-gui prompt means your X was not properly configured - that command will walk you through the config.

if all else fails, you can choose the "vesa" driver, which is the failsafe no-3d-accel driver. 

or you can edit your xorg.conf file manually, follow instructions in this thread (7th post) [http://ubuntuforums.org/showpost.php?p=887801&postcount=7](http://ubuntuforums.org/showpost.php?p=887801&postcount=7)

good luck.

---

### Post by teasum on 2006-04-16
Since this is in the "server talk" section, I might ask whether you performed a full Ubuntu install or a server install.  In the latter case, no graphical interface will be installed, and you'll have to install it on your own.  There are many HOWTOs and posts about this that you can search for.  Of course, if I'm wrong, and you did not do a server install, then something else may be up.

---

### Post by awillcott on 2006-04-20
[QUOTE=teasum]Since this is in the "server talk" section, I might ask whether you performed a full Ubuntu install or a server install.  In the latter case, no graphical interface will be installed, and you'll have to install it on your own.  There are many HOWTOs and posts about this that you can search for.  Of course, if I'm wrong, and you did not do a server install, then something else may be up.[/QUOTE]
This was a server install on an old AT system. 
I get a $ symbol

---

### Post by nanotube on 2006-04-20
[QUOTE=awillcott]This was a server install on an old AT system. 
I get a $ symbol[/QUOTE]

ah, that explains it. by default the server install does not install any graphics stuff, just the base system. 
if you want to get graphics, you should run this command:
```
sudo apt-get install xubuntu-desktop
```
that would install the light-weight XFCE desktop environment (which i recommend over regular "ubuntu-desktop" since you said your system was old).

once that's installed, run "startx" from commandline, and that should start the gui (though you may wish to reboot for good measure).

---

