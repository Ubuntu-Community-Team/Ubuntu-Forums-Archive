---
title: "LAMP security - Netcat"
date: 2008-03-13
forum: Security Discussions
---

### Post by samiux on 2008-03-13
Hi all,

I have a Ubuntu LAMP server.  My friend told me that crackers can make a backdoor or hack my server by mean of Netcat.  How can I protect my web server from such kind of attack?

I searched my server and find the software Netcat inside.  By means of security, can I uninstall it?  I found that it will uninstalled with "ubuntu-mininal" also.  Is it safe to uninstall them all?

By the way, I googled and found that almost all the posts about Netcat is for hacking a Windows server.  Is it safe for Ubuntu?

Samiux

---

### Post by The Tronyx on 2008-03-13
Netcat is regarded as a network "swiss army knife" and it really is.  You do not necessarily build a backdoor using netcat, you can, but it isn't like...a framework.  Netcat is in its simplest form, used to read and write across TCP and UDP connections.

A netcat backdoor would be comprised of 2 parts (most likely), a listener and and sender.  This is like a client server relationship only less advanced (relatively speaking)

Netcat also is not a tool used for direct exploitation, by all means it can be and it does a fantastic job, but it is often used as an easy way to get back into a machine.

Keeping the server/client relationship in mind, a hacker could infiltrate your system then run netcat to establish a listening connection so that he can easily connect back to the system without having to execute any exploits which can sometimes take awhile to execute.

Netcat doesn't just do silly command line stuff, you can also use it to transfer files, scanning ports, script back ends...lots.

If someone hacked your machine, they might make some modifications so that when they connect to service X on your box and and run a certain command, it executes a netcat command to open up a listening port for them to connect directly to.  From there they may be able to spawn a shell, ID services or a whole bunch of stuff.  Netcat is pretty slick in the sense that once the attacker is connected from the attacking machine, to your listening machine, anything they enter shows back up in their terminal so it's very helpful in providing an inside view per se.

Hope that helps and doesn't scare you.  Your concern isn't having netcat on your machine, it's keeping someone out of your machine.  If someone were able to hack into your computer, it wouldn't matter if netcat was there or not, they'd put it there if they wanted it.

---

### Post by handydan918 on 2008-03-13
netcat is just a suite of network tools. Sure, you can remove it from your system. The problem is the cracker who is trying to use the tool on his own computer in an attack against your server. 
And there really isn't any way to answer such a broad question. If you have a net-facing server, and you aren't sure how to secure it, you should do two things asap:

1) Schedule regular backups. check into rsync and cron. They will to the heavy lifting for you. Do it now. Right away.

2)start educating yourself by checking out security sites, and even hacker sites. insecure.org is one, metasploit is another.
If those places don't scare you, sell your server.

---

### Post by samiux on 2008-03-14
2point0 and handydan918,

Thank you for your information.

Samiux

---

