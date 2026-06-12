---
title: "Server vs. Desktop"
date: 2006-07-29
forum: Server Platforms
---

### Post by dolphin_1 on 2006-07-29
Simple question but I can't find the answer.  What can the Server version do that the Desktop version can not be configured to do?

And if I chose to stick with the destop version, can you point me to a document that explains how to set up a file server and mail server with the Desktop?

---

### Post by MonkeyNet on 2006-07-29
Advantage of the Server platform is that Gnome, KDE, or X are not installed which most servers wouldn't run. Another advantage is LAMP (Linux Apache MySQL PHP). It's an easy way to setup a box for web with everything you really need already installed.

I use the desktop edition of Ubuntu on my home network as a server, mainly because I have a switchbox and use it to do some coding which I use eclipse. 

The setup though between the two is exactly the same, although if you have gnome, kde, x then you can use things like synaptic package manager to search for and d/l extras.

All in all, I think it all comes down to your familiararity of Linux and what suites your taste.

Hope this has been insightful :rolleyes: 

Cheers,

Andrew

---

### Post by drivel on 2006-07-30
If you want your computer became a server,It's better not run x-window on it.and also you can install Apache2,Php5 and mysql to let a desktop became a server

---

### Post by houstonbofh on 2006-08-01
> **drivel said:**
> If you want your computer became a server,It's better not run x-window on it.

I hate these comments.  GUIs make things easy.  They are good for that reason.  They do add some weight.  Nothing comes free...  That all said, there are ubuntu-desktop and xubuntu-desktop master packages that make it easy to add a desktop to a server.  There is no LAMP master package.  It is simply a matter of choosing what you want, or don't want.  A direct server option is a command line, and no service running.  Then add what you need.  LAMP is that plus Apache, MySQL, and Perl/Python/PHP.  The desktops include a lot of cruft, like sound, games, and open office.  These have to be manually removed from the desktop install, or if added with apt* -install.

However (again) there are almost no GUI tools for LAMP components.  Perhaps because so many people fell like the poster above.

---

### Post by natrixgli on 2006-08-07
If you prefer lightweight XWM such as Fluxbox, the server edition is a good place to start out. 


-n8

---

