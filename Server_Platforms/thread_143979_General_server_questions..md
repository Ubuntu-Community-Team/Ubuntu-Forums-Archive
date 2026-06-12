---
title: "General server questions."
date: 2006-03-13
forum: Server Platforms
---

### Post by darkh on 2006-03-13
Hello

Im quite new to setting up servers and I've been doing it according to one [guide]("http://davidwinter.me.uk/articles/2006/02/05/ubuntu-5-10-web-server-howto")   I've found but encountered some problems.

I've came to the point of configuring DNS through webmin. 

Im on Ubuntu 5.10, connected to internet through a router (Microcom Deskporte) with a dynamic IP.

I've set up a dynDNS domain that points to my IP but when I try to access my site I get my router configuration page. I even opened port 80 on my router. No luck.

1. What should I do to get access to my page through the internet ?
2. how can I make accounts so that other people can put thier pages there ?

Recently I've encountered another problem :

darkh@dserver:~$ lynx [http://dserver:10000](http://dserver:10000)

Looking up dserver:10000
Making HTTP connection to dserver:10000
Alert!: Unable to connect to remote host.

lynx: Can't access startfile [http://dserver:10000/](http://dserver:10000/)

What should I do with that ? Do I need to reinstall Webmin ?

---

### Post by Glut on 2006-03-13
It sounds like your router is not forwarding the request, but accepting it itself. I'd suggest checking that port-forwarding is correctly setup, because it sounds as if it isn't.
D'OH check: I'm assuming that you're not connecting from inside your router, because then it would make sense for your router to accept the connection. If this is the case, you will need to enter the hostname into /etc/hosts or the appropriate windows hosts file.

---

