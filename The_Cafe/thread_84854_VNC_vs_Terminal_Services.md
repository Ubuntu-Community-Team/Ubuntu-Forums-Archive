---
title: "VNC vs Terminal Services"
date: 2005-11-01
forum: The Cafe
---

### Post by snowjunkie on 2005-11-01
Guys,

I have been messing about for months using VNC to access my XP desktop...  the vncviewer that comes with ubuntu would just hang if I scrolled the screen at all (xp resolution is much higher).  So, I used to the kde vnc viewer client (on gnome) with better success.  Just recently it started to give me trouble too...

Then I found a thread that mentioned terminal services.... I tried it out last night and it is AMAZING.  It fits my xp desktop to my laptop resolution (wide screen) and the response is simply fantastic.  I won't be going back to VNC to access my XP desktop again!  Why didn't anyone tell me about this before?!

;-)

Al.

---

### Post by WildTangent on 2005-11-01
Ah yes, one of the few things Microsoft did right with Windows. You can use a linux app (can't remember the name, but it comes with Ubuntu) to access it via RDP (Remote Desktop Protocol) as well, but you need to play with the settings in the program before you log in, otherwise you'll be using 8 bit color, and 640x480 res :P

-Wild

---

### Post by majikstreet on 2005-11-01
??????????

---

### Post by TravisNewman on 2005-11-01
I believe the app that wildtangent mentioned is just called "rdesktop"

---

### Post by majikstreet on 2005-11-01
[QUOTE=panickedthumb]I believe the app that wildtangent mentioned is just called "rdesktop"[/QUOTE]
o_O

I'd like to do this: be able to connect from Windows to Ubuntu.

---

### Post by souki on 2005-11-01
[QUOTE=majikstreet]
I'd like to do this: be able to connect from Windows to Ubuntu.[/QUOTE]

try this [http://www.nomachine.com/](http://www.nomachine.com/) you wont beleive it
the free version is called freenx (it was in breezy-backport)

I didn't try on ubuntu (yet)

---

### Post by snowjunkie on 2005-11-01
[QUOTE=WildTangent]but you need to play with the settings in the program before you log in, otherwise you'll be using 8 bit color, and 640x480 res[/QUOTE]

Yeah, I changed it to full screen 24 bit colour... don't have to get up now and go upstairs... :p

---

### Post by WildTangent on 2005-11-01
[QUOTE=panickedthumb]I believe the app that wildtangent mentioned is just called "rdesktop"[/QUOTE]
That's the one :P Very useful for administering my home network, because all the other computers are Windows, though I'm working on changing that ;)

-Wild

---

### Post by UbuWu on 2005-11-02
[QUOTE=panickedthumb]I believe the app that wildtangent mentioned is just called "rdesktop"[/QUOTE]

Tsclient (apps -> internet -> terminal server client) is much easier to use.

---

### Post by snowjunkie on 2005-11-02
[QUOTE=UbuWu]Tsclient (apps -> internet -> terminal server client) is much easier to use.[/QUOTE]
That's the one I'm using and it's perfect.

---

### Post by majikstreet on 2005-11-02
can you access a WinXP remote desktop from the internet? Like if it's not on your lan? how? I forget, is the windows remote desktop easy to start for a person who's not too good with computers?

---

### Post by pete on 2005-11-02
[QUOTE=majikstreet]can you access a WinXP remote desktop from the internet? Like if it's not on your lan? how? I forget, is the windows remote desktop easy to start for a person who's not too good with computers?[/QUOTE]

You can, as long as you know the public IP address of your WinXP machine.  Also, if you have a router/firewall between that machine and the internet, you would need to tell it to forward the RDP port (3389, I believe) to the WinXP box.

Of course, you've then made it possible for anyone *else* on the Internet to access your WinXP machine via remote desktop, so proceed with caution...

---

### Post by majikstreet on 2005-11-02
unless you use a password :)

---

### Post by pete on 2005-11-02
That's why I said "possible" :>    Just make sure the password is reasonably complex.

---

### Post by majikstreet on 2005-11-02
ahh......

I'll have to get into my grandmothers router (set up by my uncle so he can use his laptop in their house.. now it's mainly used for their tivo+wireless) to forward that port in case she ever should need help :)

---

