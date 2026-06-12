---
title: "can't shutdown"
date: 2009-04-01
forum: The Cafe
---

### Post by TamisLaan on 2009-04-01
Alright so is this part of the April fools day? The shutdown button has disappeared. :lolflag: ooh and sins i am writing this here any way, how do i shutdown from console?

---

### Post by smartboyathome on 2009-04-01
if you want to shutdown from console, use sudo shutdown -h now

---

### Post by tjwoosta on 2009-04-01
>  	
Alright so is this part of the April fools day? The shutdown button has disappeared.

i cant be 100% because im not using ubuntu, but im pretty sure thats not an april fools joke

you can add or remove buttons from the panel by right clicking on it

---

### Post by jdong on 2009-04-01
> **tjwoosta said:**
> i cant be 100% because im not using ubuntu, but im pretty sure thats not an april fools joke

you can add or remove buttons from the panel by right clicking on it

This is NOT an April Fools joke. Ubuntu has not deployed any April Fools jokes to its users since the Warty Warthog days (when a somewhat hairy parody of the welcome screen picture was deployed to beta testers).

---

### Post by billgoldberg on 2009-04-01
> **smartboyathome said:**
> if you want to shutdown from console, use sudo shutdown -h now

actually it's 

sudo shutdown -h NOW


The NOW has to be recited out loud screaming, using your best Arnold Schwarzenegger impression.

---

### Post by dragos240 on 2009-04-01
Hmm, i just always used:
```

sudo halt

```

---

### Post by swoll1980 on 2009-04-01
I never understood why I need root privileges to do it in the terminal, but using the GUI I don't.

---

### Post by dragos240 on 2009-04-01
> **swoll1980 said:**
> I never understood why I need root privileges to do it in the terminal, but using the GUI I don't.

I do, GDM the display manager or KDM if you use KDE, will startup with root privileges, it will allow GNOME and KDE things without sudoing, GNOME uses root privileges, a normal terminal does not.

---

### Post by swoll1980 on 2009-04-01
> **dragos240 said:**
> I do, GDM the display manager or KDM if you use KDE, will startup with root privileges, it will allow GNOME and KDE things without sudoing, GNOME uses root privileges, a normal terminal does not.

Thanks for the explanation.

---

### Post by jdong on 2009-04-01
> **swoll1980 said:**
> Thanks for the explanation.

There are dbus hooks that the GUI uses to request a shutdown; the authorization to do this can be set via PolicyKit; by default the foreground active user is always allowed to shutdown/restart; but you can configure that otherwise if you dont' want your users to shut down the system.


These same hooks can be accessed from the command line but it's not obvious. The GUI does not directly use the shutdown -h now command.

---

