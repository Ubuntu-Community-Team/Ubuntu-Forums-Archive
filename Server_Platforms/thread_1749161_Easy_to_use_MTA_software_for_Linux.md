---
title: "Easy to use MTA software for Linux"
date: 2011-05-04
forum: Server Platforms
---

### Post by Anterax on 2011-05-04
I am someone that does not like complex software.

At the moment my front counter business computer is also my web and mail server for a website. This is how its setup:

Computer (Linux)
-------Web server
-------Virtual Computer (Windows XP)
--------------MTA server/client


Soon I will be buying another computer and making the current counter computer a dedicated server.

I will also be hosting a second website and I am going to host my websites as follows:

Computer (Linux)
-------Virtual Computer 1 (Linux)
--------------HTTP server
--------------MTA server/client
-------Virtual Computer 2 (Linux)
--------------HTTP server
--------------MTA server/client


I only have one Windows XP retail license and I would like to get away from Windows, so the point of this thread is I am looking for some very easy freeware MTA software to use with Linux.

It doesn't have to be open sourced, I just want an easy to use application which won't take much to learn and setup.

I currently use MERCURY, which unfortunately runs on Windows only.

:P Before anyone suggests it... it has problems running under WINE.

Does anyone have any suggestions for software?

---

### Post by volkswagner on 2011-05-04
An easy to use software is a relative term....

First may I ask why have two HTTP servers, you will have additional configuration for listen on port 80 from your router.  The same will hold true for your mail server.

Why not run one Linux virtual server for mail, and the second for HTTP?  You can use name based virtual servers inside apache2 for multiple domains hosted on one server.

Look into Citadel for your all-in-one mail server.  It is dead simple and allows multiple domains.

The standard for MTA in Ubuntu is [Postfix]("https://help.ubuntu.com/10.04/serverguide/C/postfix.html"), alternate would be [Exim4]("https://help.ubuntu.com/10.04/serverguide/C/exim4.html").  I can't say which is easiest.

---

### Post by i.r.id10t on 2011-05-04
I would take the new computer, put Debian or Ubuntu on it (I'd go w/ debian but I like the command line) and then put ISPConfig on it.  ISPConfig will handle your multiple domains for both web and email, has an easy to use web based interface, and Just Works.

---

