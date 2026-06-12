---
title: "tightvnc on Ubuntu Desktop"
date: 2017-02-07
forum: Server Platforms
---

### Post by Revo99 on 2017-02-07
Hi Everyone,

Was struggling with this last night. Also dug around for a few hours on the internet and feel I am going in circles as most guides are for Ubuntu Server.

I have setup Ubuntu Desktop that I plan to use as a home sever. I want to be able to to setup  Tightvnc Server with it. Why tightvnc? Because its a different desktop where people can't see what you're doing. 

Having tried to set this up last night I keep getting a grey screen with no desktop shown when I login from the client. Does anyone know the correct settings I should put in my [COLOR=#3A3A3A][FONT=monospace]~/.vnc/xstartup file?

A alot of online guides refer to installing [/FONT][/COLOR][COLOR=#3A3A3A][FONT=monospace]xfce4[/FONT][/COLOR][COLOR=#3A3A3A][FONT=monospace] or equivalent. But I know Ubuntu would already have a window manager included. 

Thank in advance for your help [/FONT][/COLOR]:D

Revo99

---

### Post by wildmanne39 on 2017-02-07
*Thread moved to **Server Platforms**.*

---

### Post by Revo99 on 2017-02-07
Thanks wildmanne39. If anyone has an ideas they are welcome. Thanks

---

### Post by steeldriver on 2017-02-07
IIRC the issue with trying to use the existing Ubuntu (unity) desktop is that it renders poorly - if at all - over VNC

It used to be possible to use the unity2d/metacity interface, but I'm not sure if that's possible any more

The reason for suggesting xfce4 is probably that it gives a reasonable balance of features versus speed - you could use any lighter weight desktop / window manager of your choice

---

### Post by Revo99 on 2017-02-07
Thanks very much for the explanation. So the problem now is I already have Ubuntu desktop installed. 
Is it going to hurt my setup if I install xfce4 alongside gnome.
I am assuming yes. If so does it mean I just can't use tightvnc with Ubuntu Desktop?Sorry slightly out of my depth in this regard. 
Thanks

---

