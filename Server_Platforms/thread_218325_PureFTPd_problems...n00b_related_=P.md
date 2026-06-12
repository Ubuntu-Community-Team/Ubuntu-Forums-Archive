---
title: "PureFTPd problems...n00b related =P"
date: 2006-07-18
forum: Server Platforms
---

### Post by HedonismBot on 2006-07-18
](*,) 

Installed 6.06 LAMP, works great...problems with PureftpD install like crazy...as in, will not let me log onto the server even though it connects (shows me the PureFTPd login message, so I know it's not a port issue)

I log on with root and it gives me: 

220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 12:02. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (10.10.10.144:administrator): root
331 User root OK. Password required
Password:
530 Login authentication failed
ftp: Login failed.


I log onto it using my test user (zoidberg) and I get an entirely different error:

220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 12:02. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (10.10.10.144:administrator): zoidberg
331 User zoidberg OK. Password required
Password:
421 Service not available, remote server has closed connection.

huh?!

This is a clean install based on a guide posted to these forums for 5.10, but when I look up these problems online, I get more people having problems, and no answers. I've editied my conf's, linked things, changed settings in the files as perscribed by the developers own site...but still endless login errors...

Somebody please set me in the right direction :-D 

Won't someone please help Zodiberg?

---

### Post by va3uxb on 2006-07-18
Are you using the latest version of pure-ftpd?  

What options are you using when you start it up?  I'm using pure-ftpd on Dapper and it has worked fine for me.  Actually it worked fine for me with Breezy as well.

I have the latest version, 1.0.21 and I'm using the following options to start the server:

pure-ftpd -E -H -s -u 100 -p #####-#####

The -u 100 tells it not to allow any connections from users with uid of less than 100, so in other words no root access on ftp.  -E does not allow any anonymous connections, -H tells it not to resolve hostnames, and I forget what -s is for.  the -p #####-##### tells it what port range to use for passive / data transfer, I specify it to match the port range I have open on my firewall.

When you are logging in, are you local (like on another machine on your own network) or are you trying from outside on the internet?  Does it work inside your network?

-Stephanie

---

### Post by XplOzIOn on 2006-10-11
I been using latest pure-ftpd compiled from source using an mysql db. So far i have just 2 problem that i have not been able to fix and no one have been able to help me. Anyways. Why dont you use this [http://machiel.generaal.net/index.php?subject=user_manager_pureftpd]("http://machiel.generaal.net/index.php?subject=user_manager_pureftpd")

Works pretty nice and is nicer//faster for me imho

Good luck

---

