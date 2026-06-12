---
title: "HowTo configure the server to use X11Forwarding for ssh?"
date: 2005-12-01
forum: Server Platforms
---

### Post by grossnik on 2005-12-01
Dear all

I can't configure the ubuntu server to use X11 client apps (like xterm, xclock, ..)

Here is what I did:


SERVER
======

$ sudo apt-get install openssh-server

/etc/ssh/sshd_config
--------------------
X11Forwarding yes
X11DisplayOffset 10

$ sudo /etc/init.d/ssh restart
$ sudo apt-get install xterm

CLIENT
=====
(running a X11 server)
$ ssh -X ubuntu@192.168.0.23

$ echo $DISPLAY
=> empty

I expect localhost:10.0


I want to install Oracle on the server - and they use a java awt installer => X11 is needed.

How can I configure the server to use  X11Forwarding for ssh?

Thx for any help!

Kind Regards
bruno

---

### Post by grossnik on 2005-12-01
ok 
I got it

missing was:

SERVER
======
$ sudo apt-get install xauth

(why does xterm not depend on xauth ?)

---

### Post by papayiya on 2006-01-18
Awsome thanks,
I was having the same problem

George

---

