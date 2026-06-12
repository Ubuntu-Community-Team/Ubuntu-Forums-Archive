---
title: "Novice starting out"
date: 2008-04-24
forum: Server Platforms
---

### Post by Griffi09 on 2008-04-24
I have very, very little linux experience, but i'm setting up a web server and i was really excited about using ubuntu's new release.  8.04.

How did everyone else become and expert on this?

any books or classes to suggest?

Should i just go into using the desktop version, being used to GUI interfaces?

Advice is welcome.

---

### Post by secondstage on 2008-04-24
I just got interested in HTML a year ago, and switched to Ubuntu Studio 7.10 about 4 months ago. I would suggest any SAMS Teach Yourself series books; I have used them for HTML, and Java. I have installed apache2 and got my new computer build up and running as a web server. Hardy looks good, but I'll wait a 2-3 weeks before I update. I use the desktop version of 7.10 only because I'm too deep into this distro now. The only difference, that I know of that, is that the server edition comes with alot more server related packages, but you can install the GUI on it just like a desktop.

---

### Post by Michael Allison on 2008-04-24
I actually find "for dummies" books to be really helpful as well.

---

### Post by archgriffin on 2008-04-24
I wouldn't bother with the GUI even for your first LAMP server. Not having it forces you to use command line and make you more comfortable with it. That way when you have a GUI but need something done by command line you won't be afraid of it. The best way for my to learn was give myself a project for force my way through it. 

I started with wanting a file server in my home, which was done with FreeBSD. Later in a college class we had to build a webserver so I used the article [http://www.littlewhitedog.com/content-72.html](http://www.littlewhitedog.com/content-72.html) as a step up to what I already knew (not much), but it got me to recompile a kernel and a few other things.

I've tried books, and they are helpful to me as a reference, but google and here is where I normally go to first. 

Eventually just getting a system and playing with it, giving yourself a goal, will make you learn it. Also you'll read things that fix your problems or just get done what you want, if you take a moment to at least understand a part of WHY it worked, your knowledge increases. 

Also, never be afraid to ask even what might seem like a simple question, remember everyone had to learn it at some point too.

---

### Post by adamos on 2008-04-25
Books always put attention to details..

Start Beginning Ubuntu server Administration - from novice to professional  from Apress and then to go more in depth pick up oreillys linux server administration.

As for the GUI.. in real world they dont use GUI for server administration, so it would be better to start getting more comfortable with cli.

Thanks,

Adam

---

### Post by gtdaqua on 2008-04-25
> **adamos said:**
> Books always put attention to details..

Start Beginning Ubuntu server Administration - from novice to professional  from Apress and then to go more in depth pick up oreillys linux server administration.

As for the GUI.. in real world they dont use GUI for server administration, so it would be better to start getting more comfortable with cli.

Thanks,

Adam

True enough. Its Windows concept to administer servers via GUI. Learn CLI. You will really enjoy. I initially hated the idea of administering a server via CLI but now I see the picture.

---

### Post by Griffi09 on 2008-04-25
Thanks for everyone's advice, I'm going to stick with the cli.  Some of this was coming back to me as i do it.  And i really want to learn this as a production enviroment would handle it.

I may pick up a book or two.

Thanks and you'll hear from me again.

---

### Post by member54321 on 2008-04-30
You said > I wouldn't bother with the GUI even for your first LAMP server.

A usefull text program to give you some of the advantages of X without X is twin.

It is a text windowing system, ugly but works well. If only they would support ansi drawing characters cood look nice too.

Now the reason I replyed. 

I set up some servers for a Red Hat 9 course 4 years ago. Trying to set up LAMP + Print Server for a Home network only not as an internet server.

In Red Hat to let each user publish his own page you edited a configuration file and made a directory ~/public_html
and a file ~/public_html/index.html the users page. The page could
then be seen as [http://localhost/~username/](http://localhost/~username/) or from another pc as
[http://host-name-or-ip/~username/](http://host-name-or-ip/~username/). But the configuration file used by Red Hat 9 seems to be not used in Ubuntu 8.04 could anyone give
me instructions on how to let users publish easly on Ubuntu and how to set up an annomious print server  for access  by Mac OSx, Windows Vista and Ubuntu clients.

Thanks!

Charles

---

