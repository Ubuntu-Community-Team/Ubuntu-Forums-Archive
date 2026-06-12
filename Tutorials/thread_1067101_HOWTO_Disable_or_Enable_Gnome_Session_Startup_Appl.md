---
title: "HOWTO: Disable or Enable Gnome Session Startup Applications from Command Line"
date: 2009-02-11
forum: Tutorials
---

### Post by d2globalinc on 2009-02-11
**[SIZE="3"]HOWTO: Disable or Enable Gnome Session Startup Applications from Command Line[/SIZE]**

- As usual I am not responsible for you screwing up your install by using these instructions the wrong way! - 

So I looked around, and just couldn't find out how to do this without using the GUI (Which by the way is SYSTEM->PREFERENCES->SESSIONS)

It looks like by default session startup options are located in the following directories:

/usr/share/gnome/autostart/
/usr/share/autostart/
/etc/xdg/autostart/
and then every user can have their own autostart options located in
~/.config/autostart/ 
(the above translates to: /home/<username>/.config/autostart/ )

So if you want to disable a startup option from command line you would just open a terminal window and remove or as I perfer - rename - the startup options corrisponding .desktop file.  For example, to disable the check for new hardware on every login for every user - you could do this:

- Open a terminal window
- do the following:

```

sudo mv /etc/xdg/autostart/jockey-gtk.desktop /etc/xdg/autostart/jockey-gtk.orig

```

This will rename the jockey-gtk.desktop file (which is the New Hardware Detection Application in Ubuntu) to jockey-gtk.orig - which will disable it from starting up for all users when they login.  Which was something I needed to do on a current project.

Anyway - I looked around, and I found methods for disabling startup services using the "sysv-rc-conf" package, but it was much harder to find any information about how to disable Gnome Session Startup applications without using the GUI - which was not an option for me in this case.

Hope this helps others!

Enjoy! 

Shane Menshik
D2 GLOBAL INC
[http://www.d2global.com](http://www.d2global.com)

---

### Post by aMADme on 2009-08-04
I'm searching for a way to remove skype from my autostart, but I can't find it anywhere in those places.
I added it via Startup Applications and removed it there, but it persistently autostarts everytime I login...is there anywhere else it could've hang?

---

### Post by abdusamed on 2010-09-10
I can't find the gui in lucid

---

### Post by morrcahn on 2012-12-05
You can create your own start-up app by navigating to ~/.config/autostart/ and adding a yourscript.desktop file within. In the file, modify this code for your script and place it there, making sure to name it with a .desktop.
```
[Desktop Entry]
Type=Application
Exec=/your/script/path
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=namethatwillshowinstartupapplications
Name=./your/script/path
Comment[en_US]=
Comment=
```To remove, simply delete the .desktop file from that same folder. You can also shut it off by changing the X-GNOME-Autostart-enabled option to no.

---

