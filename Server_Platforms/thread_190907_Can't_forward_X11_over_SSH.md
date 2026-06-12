---
title: "Can't forward X11 over SSH"
date: 2006-06-06
forum: Server Platforms
---

### Post by Lews Therin on 2006-06-06
Whenever I try to log in to my Dapper server with

```
ssh -X (server IP)
```

It gives me a working shell, but the $DISPLAY environment variable is still blank. I'm using openssh-server, and the default sshd_config (which seems to enable X11). Forwarding works fine from a Gentoo server I've also got, so it is not a client problem.

---

### Post by jgoguen on 2006-06-06
Does ```
ssh -Y
``` work?  I know it fixes all sorts of X forwarding problems when client side is a Mac, maybe it'll work here too.

---

### Post by Lews Therin on 2006-06-06
[QUOTE=jgoguen]Does ```
ssh -Y
``` work?  I know it fixes all sorts of X forwarding problems when client side is a Mac, maybe it'll work here too.[/QUOTE]

I love you. Not only did it fix my X11 forwarding problem, it also solved another wierd problem I was having.

---

### Post by xurizaemon on 2007-08-06
I wasn't able to forward X11 connections from one Ubuntu to another using X11Forwarding or ssh -X, but ssh -Y fixed the problem for me too. Thanks a bunch!

> 
ssh -Y enables trusted X11 forwarding. Trusted X11 forwardings are not subjected to the X11 SECURITY extension controls.


You beauty :)

---

