---
title: "See a GUI desktop when I SSH into my server ?"
date: 2012-06-24
forum: Server Platforms
---

### Post by leegold on 2012-06-24
Hi, 

Ubuntu Server 10.04 LTS,

I want to do ssh -x to my server and have a window with gui file manager like the basic things you would have in gnome or another desktop. I know this usually unnecessary for a server but it's a server on my home LAN and I think it would be "helpful".

When I ssh -x... to my server from a ubuntu desktop PC on the LAN  and I enter xterm in the cmd line already I get a good xterm window opening, so I have a basic capability. xauth is installed.

But say I install fluxbox on the server. Then I enter fluxbox on the server ssh cmd line -  it gives error message that a window manager is already running.

Obviously I am not understanding something basic on how to do this. I want to ssh into the server and have a basic desktop gui with a gui file manager and the basic gui tools. How is this done please?

I will make it so it will not start by default and only with startx, once it's working...

Thanks.

---

### Post by blackflame2996 on 2012-06-24
you need to stop the X server:
```
sudo lightdm stop
```
then start up a desktop:
```
xinit :1
```
this will bring up an xterminal
in this window enter the command to start your preferred DE.

---

