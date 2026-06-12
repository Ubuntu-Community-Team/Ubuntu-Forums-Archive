---
title: "Graphical Interface addon"
date: 2015-11-24
forum: Server Platforms
---

### Post by soamz on 2015-11-24
Hi, I have installed Ubuntu server and I want to do the basic tasks and everything like Ubuntu desktop. 
Is it possible ?

---

### Post by mastablasta on 2015-11-24
you can work in command line interface (CLI)
you can install the desktop of choice (a bit silly on a server)
you can install a web interface and manage server via web browser from another PC (e.g. Zentyal, Ajenti, Webmin, Rockstor...)

---

### Post by Bucky Ball on 2015-11-24
```
sudo apt-get install ubuntu-desktop
```

... is exactly the same as if you would have installed Ubuntu.

You might just like a desktop environment, though. There are a few to choose from. I use xfce4.

```
sudo apt-get install xfce4
```

Reboot, choose it from the 'Sessions' menu.

Just curious why you installed the server version (very lightweight and no desktop environment) when you want to 'do everything like Ubuntu desktop?' Do you only want Ubuntu's desktop environment (Unity) or ALL of Ubuntu??? :-k

---

### Post by Elizine on 2015-11-26
[COLOR=#111111][FONT=Ubuntu]To install a desktop environment, you'll need to enable package installation from the Internet (the desktop packages aren't on the server installation CD). [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Then run these commands to install a desktop environment:[/FONT][/COLOR]sudo apt-get update
sudo apt-get install ubuntu-desktop
[COLOR=#111111][FONT=Ubuntu]You should get a graphical login prompt at that point.[/FONT][/COLOR]

---

