---
title: "X11 Forwarding on New Install"
date: 2007-02-17
forum: Server Platforms
---

### Post by ltpl4y3r on 2007-02-17
Hey,
I just installed Ubuntu server and I have been trying to get x forwarding to work for a while. I installed xserver-xorg-core and openssh-server. Also I installed xterm to give me something to open. I've been using Xming, as my main machine runs XP. Xming works with my other laptop that is running a desktop version of ubuntu. 

Question is: Is there more that I need to install? Did I just miss something?

Thanks

---

### Post by elst on 2007-02-18
You need both an SSH client and an X server on the desktop. The remote end just needs an SSH server and whatever X applications you want to run. I haven't done X11 forwarding from a Windows desktop, so unfortunately I can't be more helpful.

---

### Post by jtc on 2007-02-18
As elst mentioned, you need to install a X-server on your XP. [Cygwin]("http://www.cygwin.com/") can provide you with one.

---

### Post by ltpl4y3r on 2007-02-18
OK, let me restate this...

I've got three computers: my main one, laptop, and server.
Main = Win XP
Laptop = Ubuntu desktop (dapper)
Server = Ubuntu Server 6.1 (LAMP setup)

I use xming ( sort of lite and mobile Cygwin) on Main to forward an xterm from Laptop. Works great. I tried to do the same thing with server, but I could not get it to work. I had Openssh-server and xserver-xorg-core installed on the server, as well as xterm, and it still does not work. I was wondering if there is anything else I need to install on the server to be able to get it to forward correctly.

---

### Post by jtc on 2007-02-18
Do you have the X11Forwarding directive set in your /etc/ssh/sshd_config?

EDIT: Never mind. That directive is important, but it is enabled by default. Probably something else.

---

### Post by johnblade on 2007-03-08
Try installing the xserver-xorg package rather then just the core... and make sure you ssh into it with the -X argument on unix.

---

### Post by Mr. C. on 2007-03-08
Unless I'm forgetting my X11, the X server is displaying the graphics, and the X clients send the output (locally or over the wire) to the X server.  Therefore, the OP's Server machine would not need the X11 server running; only the X11 clients.

It does seem that the tunnel is properly setup to forward X11.

MrC

---

### Post by plumcreek on 2008-06-04
Install xauth and x11-apps:
```
sudo apt-get install xauth x11-apps
```

Log out and then ssh back in (with the -X flag):

```
ssh -X username@hostname
```

Now try running xclock (installed when you installed x11-apps):

```
xclock
```

The clock should appear (assuming you are connecting from a graphical Linux host).

---

