---
title: "mfc240c printer on LAMP server"
date: 2007-09-03
forum: Server Platforms
---

### Post by OldGaf on 2007-09-03
I am trying to setup an LAMP server with no GUI in an effort to get more comfortable with the inner workings of Linux.

I have Apache running fine with virtual hosts and CGI working too. My only problem is this server is also our home printer server. I have an mfc240c and had no problem getting it to work with my Linux and Winblose systems when I had a desktop installed, but can't seem to get it going on the server.

I have the following installed:
> mfc240clpr-1.0.0-9.i386.deb
mfc240ccupswrapper-1.0.0-9.i386.deb
And I get no errors.

When I run lpq I get:
> lpq: lp: unknown printer

nmap shows the following:
> PORT      STATE SERVICE
21/tcp    open  ftp
22/tcp    open  ssh
80/tcp    open  http
631/tcp   open  ipp
3306/tcp  open  mysql
so I know that cups is listening on port 631.

I then got desperate and disided to cheat a little and installed webmin.
When I go under "Hardware/Printer Administration" I see the following:
> [IMG]http://www.nialm.com/forum-pics/webmin1.png[/IMG]

When I try to print a test page I get this:
> [IMG]http://www.nialm.com/forum-pics/webmin2.png[/IMG]

So what gives? Is there a file I need to edit? Everything I have found tells me to add the printer through the GUI..... not much help on a server :(

Also, should I be able to remotely access the CUPS page from my desktop pc?
i.e. "http://**192.168.0.111**:631" instead of "http://l**ocalhost**:631"

Any help would be most appreciated.

---

### Post by zero-9376 on 2007-09-03
is cups installed

---

### Post by OldGaf on 2007-09-03
Yes, I installed cupsys before I installed the driver/wrapper. At that point I saw 
> 
PORT      STATE SERVICE
631/tcp    open    ipp 
added to the list when I ran 
> sudo nmap localhost -v 
I assume this is cups listening?

BTW:
I just got it working using samba so the server obviously knows about the printer, and it works if I send it raw data from my other Linux boxes so the drivers must be installed..... ?

I would really like to figure this out as it makes no sense to me (tho I have been told that "it is easy to confuse a stupid person" :confused:)
I would like to be able to connect by IP and not have to use samba.

---

