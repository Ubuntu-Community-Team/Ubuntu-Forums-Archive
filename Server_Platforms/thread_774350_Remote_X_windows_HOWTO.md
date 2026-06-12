---
title: "Remote X windows: HOWTO"
date: 2008-04-29
forum: Server Platforms
---

### Post by archwaypms on 2008-04-29
How do you run remote X-windows applications or desktop. This must be simpler thant it appears to me.   

I have used Unix for years but never X-windows remotely, so newbie in this field and quite confused for once

I have Ubuntu 6.06 Remote Virutal Private server, so I do not have access to any console.  I have root access and SSH and got SAMBA, plesk, apache and my webserver and domains all working well. I have zebedee as another tunnel. 

I suspect not all the X-windows functions are installed, although X11 directories exist.  VNC seems a good approach but it needs X and things running on the server, and I am not sure what or how.

At home I have putty.

What do I need to install or check that are installed on my server, and what do I need to do at my home client end, assuming I will run X-windows via SSH.

Thanks.

Gerry Bulger
Gerry

---

### Post by Ek0nomik on 2008-04-29
> **archwaypms said:**
> How do you run remote X-windows applications or desktop. This must be simpler thant it appears to me.   

I have used Unix for years but never X-windows remotely, so newbie in this field and quite confused for once

I have Ubuntu 6.06 Remote Virutal Private server, so I do not have access to any console.  I have root access and SSH and got SAMBA, plesk, apache and my webserver and domains all working well. I have zebedee as another tunnel. 

I suspect not all the X-windows functions are installed, although X11 directories exist.  VNC seems a good approach but it needs X and things running on the server, and I am not sure what or how.

At home I have putty.

What do I need to install or check that are installed on my server, and what do I need to do at my home client end, assuming I will run X-windows via SSH.

Thanks.

Gerry Bulger
Gerry

You can run X through SSH by logging in to the remote server like so:

```
ssh -X yyy@zzz
```

On your client computer, you simply need the X window environment.  If it's Windows you can use Cygwin or XMing.  If you are on a client Linux box then you don't need to do anything except make sure you have openssh installed and a running X environment.

---

### Post by archwaypms on 2008-04-29
Thanks.   I suspect it is as simple as that, but my remote server does not have a console, so there is not default X environment and desktop setup such as KDE or gnome, or simpler solutions.  I think I must do more work on the server.

Gerry

---

### Post by koenn on 2008-04-29
> **archwaypms said:**
> Thanks.   I suspect it is as simple as that, but my remote server does not have a console, so there is not default X environment and desktop setup such as KDE or gnome, or simpler solutions.  I think I must do more work on the server.

Gerry
you don't need those on the server. On the server, you just have applications, and they direct their output to windows created on, say, a linux pc somewhere else. If you're in fromnt of that linux PC, you can interact with the application on your desktup, although the app is actually being executed on the server. 

Here's a brief intro : [http://users.pandora.be/mydotcom/howto/linux/xremote.htm](http://users.pandora.be/mydotcom/howto/linux/xremote.htm)

---

### Post by archwaypms on 2008-04-29
Dear Keonn

Thanks a LOT for that last link.  Mentions the bleeding obvious,which made immediate sense to me, and exactly the same as the Linux/unix and the text or web based services programmes I have used for years: it runs on the server with emulation on the client

I will now go away and play. 

It is obvious now of course, but sometimes it needs someone ot point out the obvious....x-windows runs on the client...not the server

I was confused by the vnc solutions that expect both client and server on the server...a desktop running there, which is the usual home/domestic setup.


Gerry

---

### Post by koenn on 2008-04-29
Yeah, when you got used to typical client-server architecture, server-based computing, and especially X-forwarding, requires that 'click' in your head, after which everything falls into place.

---

### Post by Jeztastic on 2008-04-30
Hope you don't mind my hopping in on this thread, but I have tried following the guide, but got this error output:

```
jez@jez-laptop:~$ ssh -X jez@server mousepad
jez@server's password: 
Warning: No xauth data; using fake authentication data for X11 forwarding.
Xlib: connection to "localhost:10.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key

(mousepad:5349): Gtk-WARNING **: cannot open display:
```

Wassup with that?

EDIT: Ok, sorted, it all works now!

---

