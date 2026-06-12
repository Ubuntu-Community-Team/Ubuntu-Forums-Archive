---
title: "multiple screens?"
date: 2012-03-11
forum: Server Platforms
---

### Post by wlraider70 on 2012-03-11
In the cli environment is there a way to have multiple terminals.
I'm thinking of the shell that one can use on Ubuntu desktop.

IS there another way to accomplish giving the system a 2nd command while it is still executing the 1st?


Also is there a differences between terminal and consul which am I at in server version?

---

### Post by kevdog on 2012-03-11
I thought buttons f1-f6 would open up multiple terminals which you could use.

---

### Post by Kirboosy on 2012-03-11
You are referring to a [TTY]("http://linux.about.com/od/commands/l/blcmdl4_tty.htm")

In order to access the different TTY use the keycodes

CNTL+ALT+F1 (F2, F3, F4 are all different TTYs) To return to your original just simply press ALT +F7

EDIT: Another option would be the handy program [BYOBU]("https://help.ubuntu.com/10.04/serverguide/C/byobu.html")

---

### Post by volkswagner on 2012-03-12
Yet another option would be to install screen.
```
sudo apt-get install screen
```
```
man screen
```
It has a learning curve and there are some good how-to's on the net.  It really shines when combined with ssh and the ability to reattach to a session.

---

### Post by nothingspecial on 2012-03-12
And there is [[COLOR="Blue"]byobu[/COLOR]]("https://launchpad.net/byobu")

---

