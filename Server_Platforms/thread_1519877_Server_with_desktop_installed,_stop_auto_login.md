---
title: "Server with desktop installed, stop auto login"
date: 2010-06-28
forum: Server Platforms
---

### Post by canabal on 2010-06-28
Hey all,

I recently setup Ubuntu server as a media server for myself.  I use "playstation media server" for sharing my media with my ps3 and so I was forced to install ubuntu-desktop.  I am using the server headless and so I setup "vncserver", but for some reason, it is also autologging in the original X session, so 2 sessions are going and killing my memory.

I have tried just using the original session using X11VNC, but it is much slower than using vncserver, and almost unusable I have found.

So my question: how do I stop the original X session from logging in automatically (I never set it up to do this, it did it automatically).

edit: just to add, I am running 10.04 server, amd64

---

### Post by krunge on 2010-06-28
> **canabal said:**
> 
I have tried just using the original session using X11VNC, but it is much slower than using vncserver, and almost unusable I have found.

Just a guess, try adding the -noxdamage option to the x11vnc cmdline.  You can search these forums with 'noxdamage' for more info on the problem it works around.

---

### Post by canabal on 2010-06-29
> **krunge said:**
> Just a guess, try adding the -noxdamage option to the x11vnc cmdline.  You can search these forums with 'noxdamage' for more info on the problem it works around.

Funny how I missed that option on this server, yet I have it on my desktop... I had figured it was to do with it being a server and therefore a lot more resources.  Thanks a lot for the help.

Anyway, I would still like to stop autologin, does anyone have any ideas?

---

### Post by krunge on 2010-06-29
> **canabal said:**
> Funny how I missed that option on this server, yet I have it on my desktop... I had figured it was to do with it being a server and therefore a lot more resources.  Thanks a lot for the help.

So did the -noxdamage option improve the interactive response on your media server?

---

### Post by canabal on 2010-06-29
Yes it did, thanks.

---

