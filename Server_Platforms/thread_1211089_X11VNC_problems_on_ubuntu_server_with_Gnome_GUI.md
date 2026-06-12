---
title: "X11VNC problems on ubuntu server with Gnome GUI"
date: 2009-07-12
forum: Server Platforms
---

### Post by Cpt Crayon on 2009-07-12
Greetings, 

Ubuntu Nubie here. Well I thought I was doing ok.... till now. I have followed every other topic regarding this issue and nothing seems to answer my problem

I have ubuntu server 9.04 installed along with the gnome gui. also installed is x11vnc.

I have been able to get the vnc to work fine when i am already logged in to the server but as soon as i try to vnc into the server when it is at the greeter screen. vnc takes me all the way to the greeter screen - i punch in my credentials and boom..Gone.

I have followed all the recomendations from various posts but none seem to be working.

can some one with plenty of patience advise please.

---

### Post by druhboruch on 2009-07-12
Why don't you try freenx-server instead

You will find it in this repository:
```
deb http://ppa.launchpad.net/freenx-team/ppa/ubuntu/ jaunty main
```

It works quite well for me...

---

### Post by juancarlospaco on 2009-07-12
Since you have SSH you don't need VNC anymore, plus it have compression and security,
for example just...

ssh -X user@serversip programyouwanttorun

ssh -X user@serversip nautilus

ssh -X user@serversip gnome-terminal

---

### Post by krunge on 2009-07-12
> **Cpt Crayon said:**
> 
I have been able to get the vnc to work fine when i am already logged in to the server but as soon as i try to vnc into the server when it is at the greeter screen. vnc takes me all the way to the greeter screen - i punch in my credentials and boom..Gone.

I have followed all the recomendations from various posts but none seem to be working.

Have you tried the -noxfixes x11vnc option:
```
x11vnc -noxfixes ...
```
described at the url below?[indent]
[http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+noxfixes](http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+noxfixes)
[/indent]
It works around a bug in the Xorg server.

---

