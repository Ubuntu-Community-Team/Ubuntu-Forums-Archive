---
title: "Webmin with Openbsd..."
date: 2010-09-07
forum: The Cafe
---

### Post by waloshin on 2010-09-07
If you install Webmin in Openbsd are you able to install packages without using the terminal? 

And also if a hacker can easily compromise a Ubuntu Server what are the chances that they will be able to compromise a Openbsd server?

---

### Post by juancarlospaco on 2010-09-07
A hacker can not easily compromise a Ubuntu Server, 
so they will not be able to compromise a Openbsd server.

*Be a man, use the Terminal, after all it dont eat too much people per year.*

---

### Post by slackthumbz on 2010-09-07
Ubuntu and OpenBSD are both very secure by design. Ultimately, however, a system is only ever as secure as its administrator makes it.

---

### Post by DemonBob on 2010-09-07
To emphasize on whats been said already. 

Make sure you use strong passwords, if you are accessing webmin from outside on the net. USE SSL. If are accessing the machine from ssh on the outside. Make sure to use ssh-keys instead of passwords, and so on. 

Also you may want to look into jails on BSD. Running websites in there own jail on a BSD server will make it harder for anything affecting that site, to affect the base system.

---

### Post by juancarlospaco on 2010-09-07
> **DemonBob said:**
> 
you may want to look into jails on BSD.

And LXC on LiGNUx is nice too  :D

---

### Post by scottuss on 2010-09-07
> **juancarlospaco said:**
> A hacker can not easily compromise a Ubuntu Server, 
so they will not be able to compromise a Openbsd server.

*Be a man, use the Terminal, after all it dont eat too much people per year.*

Hackers can easily compromise a server if it is poorly configured, no matter what the OS.

OpenBSD is a massively secure OS until you start exposing services to the world and adding software outside of the default install.

It remains super secure, but bad configuration can be the downfall of even "perfect" systems.

---

### Post by Velnias on 2010-09-07
Well, if you install Webmin on OpenBSD and cant use terminal for package install - your OpenBSD server is doomed :-)

But yes, generaly, OpenBSD is more secure than Ubuntu.

You could talk about it in related forums, like
[http://www.daemonforums.org/]("http://www.daemonforums.org/")

---

