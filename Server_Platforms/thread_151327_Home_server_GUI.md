---
title: "Home server: GUI?"
date: 2006-03-27
forum: Server Platforms
---

### Post by ?@yk0&amp;^4 on 2006-03-27
Is there a security issue with running a GUI on a home server (which would be serving web pages, email, LAN files and printer)? It's just that the server would be easier to configure as I'm a bit of a newbie! The whole network is behind a NAT router, so this should filter out unwanted traffic right?

Thanks,
Greg.

---

### Post by harisund on 2006-03-27
I am not really a security expert (as much I would love to be) but AFAIK, it's not much of a problem, except perhaps some overhead. 

Yes, I had the GUI too, but I wouldn't start it, or let it running when I am not near the machine. 

Just my 2 cents really..

---

### Post by harisund on 2006-03-27
I am not really a security expert (as much I would love to be) but AFAIK, it's not much of a problem, except perhaps some overhead. 

Yes, I had the GUI too, but I wouldn't start it, or let it running when I am not near the machine. 

Just my 2 cents really..

---

### Post by ztx on 2006-03-29
I'm new to linux. I have installed a ubuntu as web server, and hope to install a GUI like gnome,  which package should install? and how can I start it?  thanks!

---

### Post by harisund on 2006-03-29
What exactly does installed Ubuntu as a web server mean? 

What I am assuming is that you did a "server" install, and then to make it a web server probably installed Apache2. 

Anyway, to get Gnome, you would do ```
sudo aptitude install ubuntu-desktop
```, to get KDE you would do ```
sudo aptitude install kubuntu-desktop
``` and to get XFCE you would do ```
sudo aptitude install xubuntu-desktop
```

However, before that you will have to go /etc/apt/sources.list and comment out the line that has the CD Rom name in it, and do a```
sudo aptitude update
``` first before you can do anything else.

---

### Post by sto6ma9ch on 2006-03-29
The way I understand it, the less software you have installed on a machine, the less chance that the software will have an exploitable vulnerability. The X window system, the window manager, the desktop, the calculator, etc. will all be introduced to your machine (including their vulnerabilities).

The NAT router offers some protection in that your entire network is seen as one IP address, but I don't think that the router performs packet inspection and/or drops suspicious traffic.

Eh, if someone really wanted to get into your machine (whether there's a NAT router or a firewall in the middle), he/she will get through.

---

### Post by ztx on 2006-03-29
Thanks for your reply. I install a server with apache, This is my first time run linux, I think a gui should be start easy.

---

### Post by ?@yk0&amp;^4 on 2006-04-03
Okay so it's probably best not to install a GUI or any other extra unnecessary software? That makes sense. Does anyone know of a simple Apache2 howto for Ubuntu, or do I literally just need to install it and put my files in /var/www?

Many thanks for your help,
Greg.

---

### Post by jimwillsher on 2006-04-05
If you want a server-only install (like I have) then follow the excelent howto at:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)


Jim

---

### Post by pedrotuga on 2006-04-05
[quote=gregswinford]Okay so it's probably best not to install a GUI or any other extra unnecessary software? That makes sense. Does anyone know of a simple Apache2 howto for Ubuntu, or do I literally just need to install it and put my files in /var/www?

Many thanks for your help,
Greg.[/quote]


u basicaly need to install apache and put the files in the directory u mention, yes, is as simple as that.


This command:
```
sudo apt-get install apache2
```
should do it

about the gui... well, i have a server running with breezy and at first i had gnome running... I dunno whats the problem with it... i took it away because it was not necessary as i admin it through ssh.

The thing about a GUI is that u dont need it, not that it causes any troubles.

if you want a updated and reviewed documentation on ubuntu i sugest yo go to the official wiki and insert "apache" on the search box.

you will get here:

[https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by sto6ma9ch on 2006-04-11
> The thing about a GUI is that u dont need it, not that it causes any troubles.

Any unnecessary software installed on a system is a security risk. In that respect, yes, A GUI can cause troubles on a publicly-accessible web server.

---

### Post by LordHunter317 on 2006-04-11
[QUOTE=sto6ma9ch]Any unnecessary software installed on a system is a security risk.[/quote]No, that's not necessarily true.  Unnecessary running software may be an issue, but even then, that *may* not be the case.

---

### Post by fenix03 on 2006-04-12
I recommend you try GNU SCREEN, [http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen) and ssh to administer you server box. 

It allows you to run multiple terminal sessions using one terminal window! It's like a tabbed gnome-terminal for the console except that it also allows you to start an application for example from your work place and then later when you get home you can reconnect/reattach to your screen session and continue where you left off from work. 

It's similar to VNC, it allows you to keep your console session to the server indefinitely. It's great!

I'm using it with putty (tell putty to start a remote command 'screen -RD') from my winxp box to my debian Sid server which runs exim4, dovecot, getmail, subversion and apache2. 

Total number of packages installed is at the moment 272 and around 60 processes(top) running. My dapper desktop installation has over 1000 packages installed...

---

### Post by alamba on 2006-04-12
You might also want to look at not installing a GUI such as GNOME or KDE and instead using an application like webmin to administer your webserver.

A

---

