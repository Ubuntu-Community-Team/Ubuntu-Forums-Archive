---
title: "Remote access to Files"
date: 2009-02-01
forum: Server Platforms
---

### Post by dbrine on 2009-02-01
I have 2 servers I need to access file from (Linux Servers). I'm a noob for the most part. I installed proftpd but is this the best route (will use TLS/ SSL)? I will need to access several hard drives and like I said 2 different servers from anywhere in the world. SUggestions?

I can do this with Cerebus (windows) but I know nothing about proftpd. tutorials for beginners?


Help and thanks

---

### Post by yoyoned on 2009-02-01
forget ftp.  use ssh

---

### Post by dbrine on 2009-02-01
i use ssh for local remote control. how can i do that wordwide? Tutorial, please.

---

### Post by hictio on 2009-02-01
> **dbrine said:**
> i use ssh for local remote control. how can i do that wordwide? Tutorial, please.

You can start by reading this: [Chapter 5. Remote Administration](https://help.ubuntu.com/8.10/serverguide/C/remote-administration.html), from the [Ubuntu Server Guide](https://help.ubuntu.com/8.10/serverguide/C/index.html).

Setting up Open SSH it it pretty, pretty straight forward; for what I have seeing here in the forum, the biggest bottle neck might be setting up your router to do the correct port forwarding, and, once it is up and working, securing it.

Please be aware that is you "do that wordwide?" that is, enabling access to anyone on the internet to your SSH service, you have to take some measures to tight the access to your box(es).

---

