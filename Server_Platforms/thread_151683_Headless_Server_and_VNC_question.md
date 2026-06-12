---
title: "Headless Server and VNC question"
date: 2006-03-28
forum: Server Platforms
---

### Post by hagen00 on 2006-03-28
Hi guys

I've got a question. I've got a headless server, i.e. no X server and want to install VNC. So what i did was the following. 

```
apt-get install tightvncserver
apt-get install xfonts-base xfonts-75dpi 
vi /etc/vnc.conf and change line to
$fontPath = “/usr/lib/X11/fonts/75dpi/,/usr/lib/X11/fonts/misc/”
```

I then start up the vncserver and all seems fine. But then when i try to connect with a vncclient, all i see is a grey screen with a black cross as my mouse pointer! What i want to see (and what i have seen when i connect to other vncservers) is a terminal screen where i can type stuff!

Any ideas?

Thanks

H

---

### Post by hagen00 on 2006-03-28
Maybe i should do some more research before i post..but at least now we have a complete Howto for VNC on a headless server. (Basically i needed twm and xterm installed)

```
apt-get install tightvncserver
apt-get install xfonts-base xfonts-75dpi 

vi /etc/vnc.conf and change line to
$fontPath = “/usr/lib/X11/fonts/75dpi/,/usr/lib/X11/fonts/misc/”

apt-get install twm xterm
```

Maybe i should post this as a HowTo? Pretty simple, but still took me an hour or so to research.

---

### Post by btdown on 2006-03-28
yeah a howto would be a good idea. I was under the impression that you had to have an xserver installed in order to get any kind of graphical environment... 
 
If this is the case, I should wipe clean my slow laptop and re-install Dapper and do it the way you're doing it. Would be a whole lot less resources used if I only periodically needed graphical on a vnc session and not on the console itself.
 
Maybe you could also go into some alternatives to twm...

---

### Post by hagen00 on 2006-03-29
I did do a HowTo, but it hasn't come up yet...but it's pretty simple. The steps i list in my post above cover basically everything. 

Besides twm, i suppose you could use any other windows manager (fluxbox, icewm etc). 

In case they don't work first time with the vncviewer, one would just have to take a look at the ~/.vnc/xstartup file, where it specifies what to launch on VNC server startup.

---

