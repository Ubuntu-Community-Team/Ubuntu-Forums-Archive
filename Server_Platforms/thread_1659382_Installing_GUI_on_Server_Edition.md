---
title: "Installing GUI on Server Edition"
date: 2011-01-03
forum: Server Platforms
---

### Post by urinsan3 on 2011-01-03
Hi, I just purchased a VPS and they installed a server edition of Linux, and not the desktop version. I'm using a VNC client to connect to the host so I need the GUI.

I already installed the GUI
```
sudo apt-get install ubuntu-desktop
```

and rebooted my system, I connected via VNC and everything looked like it was running smoothly (well there were massive amounts of popups with application errors, but I ignored them)

Anyways, my main issues are that I can't install anything and nothing seems to work. Firefox won't open, I tried to reinstall and get a long list of errors, java won't install either.

Any advice? I've contacted Customer support multiple times over past 24 hours and I feel bad messaging them again, plus I want to gain experience when possible.

---

### Post by bodhi.zazen on 2011-01-04
Probably not what you want to hear, but this is a poor strategy for server management, doubly so on a VPS.

You do not need X, let alone ubuntu-desktop on a server. The vast majority of running a server is editing configuration files, installing applications (apt-get) and/or starting or stopping services, none of which requires a graphical interface such a gnome.

Learn to use ssh , be sure to secure ssh with a key.

If you feel you need a graphical interface, use web tools such as webmin and/or phpmyadmin.

You mentioned there were "errors" that you "ignored" - what were the error messages ?

What type of VPS is it ? How much RAM do you have ? HD space ? Is it full now (are you out of space)?

---

### Post by stlsaint on 2011-01-04
Please give details on the errors you are getting when trying to install applications. I am unsure of how paid for VPS work but if damage is overly extensive you may want to consider having your vps provider re-install the vps to get a fresh start.

---

### Post by James78 on 2011-01-04
I second bodhi.zazen's post. Using a GUI on a server is a poor way to manage the system. You should learn to use SSH (of course, secure it down; disable root and passworded logins, change to a different port, and use keyed logins) and the command line. All you ever need to do to get a server perfectly working is use the command line; that's all that's needed. However, Webmin/Virtualmin/Usermin CAN be a great help to you; here's a guide on how to install them.
[http://wwww.ubuntuforums.org/showthread.php?t=1197883](http://wwww.ubuntuforums.org/showthread.php?t=1197883)

---

