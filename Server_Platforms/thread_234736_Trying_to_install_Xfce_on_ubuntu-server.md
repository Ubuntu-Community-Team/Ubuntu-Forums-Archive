---
title: "Trying to install Xfce on ubuntu-server"
date: 2006-08-11
forum: Server Platforms
---

### Post by SeNtiX on 2006-08-11
I need help with installing xfce on a server edition of ubuntu. I know there is Xubuntu, but i'm mainly using it as a server so I am  trying to install it just for when I need the GUI

I tried "sudo apt-get xfce4" which told me to get "sudo apt-get xfce4-panel"

After I installed it, whenever I try to run xfce4-panel, I get a
"Gtk-WARNING **: cannot open display:"

Any help?

---

### Post by CREEPING DEATH on 2006-08-12
Did you install the x-server?  [This is good info to help.]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

CD

---

### Post by SeNtiX on 2006-08-12
will try it out, tnx

---

### Post by SeNtiX on 2006-08-12
tnx for the article managed to install it, though for anyone trying it you must first enable universe packages

One last thing, i installed a vnc as well "sudo apt-get install vncserver" and started it with vncserver, though when i connect to the vnc server from another pc all i get is a grey screen and a pointer

---

### Post by SeNtiX on 2006-08-13
anyone?

---

### Post by woifi on 2006-08-13
> **SeNtiX said:**
> anyone?

i think you have to start vncserver
```
vncserver :1
```

your server should be availible at $IP:0. to speficy what you would like to run in your vnc session, you can create ~/.vnc/xstartup
```

 #!/bin/sh

 [ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
 xsetroot -solid grey
 xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
 xfce &
```

instead of xfce you can run any other windowmanager

hth

woifi

---

### Post by hfdragon on 2006-09-04
justg did the same since i also sometimes need the gui on my server :
```

sudo apt-get install xubuntu-desktop
```

And now it's just fine :-)

---

### Post by SeNtiX on 2006-09-06
hfdragon, what did you do to stop the gui from starting automatically @ startup? & to stop the gui you just kill the xserver process?

---

### Post by hfdragon on 2006-09-06
> **SeNtiX said:**
> hfdragon, what did you do to stop the gui from starting automatically @ startup? & to stop the gui you just kill the xserver process?

This I don't know... sorry, il tel this server whith the login scren on...

I don't know enough about linux to help you on this..

---

### Post by SeNtiX on 2006-09-06
tnx anyway, anyone might know?

---

### Post by FedoraUsr on 2007-07-02
Try :
:~$ cd /sbin
:~$ sudo ./init 1

---

### Post by rescdsk on 2007-11-02
I would try using the update-rc.d(8) program to remove xdm, gdm, or whatever other display manager xfce installs, from the daemons started when the system starts.  It would be something like

update-rc.d xdm remove

Hope this helps!

---

