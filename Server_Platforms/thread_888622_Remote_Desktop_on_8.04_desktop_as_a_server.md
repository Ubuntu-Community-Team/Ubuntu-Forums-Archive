---
title: "Remote Desktop on 8.04 desktop as a server"
date: 2008-08-13
forum: Server Platforms
---

### Post by mortuk on 2008-08-13
Hey all

Have a server machine. Put desktop on it as I wanted a GUI as not all the people using it will be savvie enough to use command line.

Anyways I am having issues with getting a remote desktop viewer such as VNC working. When its logged in all is fine, but when its logged off obviously no 1 can login.

I have tried setting up x11vnc and hooking it up to GDM to work from the login screen but no joy, could anyone help me out with this?

Alternativley I guess I could login from SSH and start the vnc server? Or would that not work because it needs the X server to be logged in?

---

### Post by HermanAB on 2008-08-13
Using VNC over SSH is redundant.  SSH can do everything VNC does and more, plus it is encrypted:

ssh -X -C -c blowfish user@server gnome-panel

Cheers,

Herman

---

### Post by mortuk on 2008-08-14
> **mortuk said:**
> not all the people using it will be savvie enough to use command line

I can use ssh but need vnc as well

---

### Post by windependence on 2008-08-14
I don't think you understood. Herman is telling you how to export an X session via ssh so that you actually have a desktop in your ssh session. It's much faster and much more secure.

-Tim

---

### Post by mortuk on 2008-08-14
oh right my bad :P

good stuff, will give it a try thanks (herman and windependance)

---

### Post by windependence on 2008-08-14
No problem. I wasn't sure you understood but I though you'd like it when you did. ;)

-Tim

---

### Post by mortuk on 2008-08-14
trying it on my ubuntu eee 8.04 install and its coming up with blank top/bottom bars, and the rest is what was there before ie CLI

will try it at work tomorrow (also 8.04 but non eee custom kernel) and see if thats any different

---

### Post by mortuk on 2008-08-15
heya

yeah tried it on a few PCs now and doesnt like it. It definitely changes the top and bottom panels (altho not very successfully) and does nothing for the actual desktop area

anymore ideas as its quite important I get some kind of gui radmin setup, and it must work when pc is logged out (ie if power loss and reboots)

---

### Post by windependence on 2008-08-15
Ummm learn the CLI? Seriously, I'll try to find something that walks you through the config on exporting an X session but really, when it come right down to it, I can run rings around any admin with a GUI using just the CLI.

You said you have other people using it. What does the server do and what will your other admins be doing? Maybe we can find you some tools to do just that. :)

-Tim

---

