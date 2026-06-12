---
title: "Setting things up...."
date: 2007-12-17
forum: Server Platforms
---

### Post by Help! on 2007-12-17
First off Hi. New to Linux and this forum.

I am trying to get a server up and running but an having some problems, mostly I just don't know what I am doing!  

My intent is to have a in house file serve, FTP server, Internet Server, and  RADIUS. 

So....

I have Xubuntu up and running with no problems :)
Installed PHP, Apachie, MySQL, SAMBA, and freeRADIUS.
[B]The problems are what do I do now?
How do I configure them?
And can I get a GUI?[/B]

Any help would be nice,  I foresee lots of stupid questions. :lolflag:

---

### Post by p_quarles on 2007-12-17
Well, first of all, don't run a public server until you *do* know what you're doing. :) Limit it to home use until you have a better understanding of how to secure your system.

Anyway, most of those programs come preconfigured to work immediately, for basic tasks. Beyond that, it's a question of what you're trying to accomplish. The only thing I can think of to tell you is that your public HTML directory is currently /var/www. Feel free to ask about anything else.

There are GUI frontends for some server apps -- such as Swat for Samba, and PHPMyAdmin for MySQL. Both of those are in the repos, I believe.

---

### Post by mmichalik on 2007-12-17
you can also use Webmin as a front end GUI.

It's very easy to setup and has modules for a lot of different applications.

[www.webmin.com](www.webmin.com)

---

