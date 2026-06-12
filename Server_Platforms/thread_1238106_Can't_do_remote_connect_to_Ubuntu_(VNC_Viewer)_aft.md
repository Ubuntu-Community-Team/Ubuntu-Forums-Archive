---
title: "Can't do remote connect to Ubuntu (VNC Viewer) after reboot"
date: 2009-08-12
forum: Server Platforms
---

### Post by staphylo on 2009-08-12
Hello, I have Ubuntu 9.04 Desktop(Running as server)
My problem is that I can only connect to my home server when Ubuntu is already logged on but when my server need to be restarted, after fully rebooted at the login screen, it continues to do not respond to request's from my VNC Viewer(Running on Windows XP).
Resuming..I can only connect when Ubuntu is already manually logged on

I really need to manage my server fully remotely, if not I always will need to change DVI cable from one to another

:(

---

### Post by cdenley on 2009-08-12
I don't know of a way to make vino work from the login prompt. You can use vnc4server, which allows you to create new sessions. It may take some configuration. You can also use SSH with X forwarding, but I'm not sure how to make that work in Windows. You could also enable auto-login. I would recommend that you familiarize yourself with the terminal, which is the only way a server should be administered. Then you could simply use SSH, simple and secure.

---

### Post by staphylo on 2009-08-12
But I can't configure, I installed VNC Server but problem is still the same... 
Someone should help

---

### Post by gobbledigook on 2009-08-13
hi there!

i use vncserver on a headless machine with no problems. I think your issue is that vncserver is not being loaded as a daemon on startup? so it is not running automatically. I have the same issue but have never been able to get a daemon to work! 

So the solution is simply to ssh into the box using a client like putty on port 22, and run command

```
vncserver :1
```

after its loaded you can exit and then access using vnc client of your choice:) this command only loads default settings if you try 

```
vncserver --help
```

that will give you a full list of functions. vnc can be a bit sluggish, i prefer the cli, takes a bit of getting used to but is a lot more powerful and you can daisy chain commands:)

hope this helps!

Dan

---

### Post by cdenley on 2009-08-13
I haven't used a linux vnc server in years, but I always started it from a ssh session since I tunneled through ssh to connect to vnc anyway. I wouldn't use vnc over the internet without an encrypted tunnel, but it sounds like you will be using it over the LAN. What I meant when I said that option may take some configuration was possibly a startup file that started gnome when you connected, and also an init script or something to start it as a daemon.

---

