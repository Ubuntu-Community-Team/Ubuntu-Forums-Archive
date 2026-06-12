---
title: "Ubuntu Server for Dummies"
date: 2006-07-28
forum: Server Platforms
---

### Post by z33k3r on 2006-07-28
Does such a thing exist or something like it? I am a noob to *nix and have successfully setup a Ubuntu 64bit Server on a dual Opteron system. I just now need to know how to operate it and administrate it. I know that Ubuntu is based off of Debian, so I guess, is there any book/tutorial/guide to noobs like my self that don't neccessarily need all the in dept explination of what bianary is and hex decimal is, but rather, something that says, "to do this, do this" or "if this happens, you will want to do this" or "this is structured like this, so if you want it to act different, do this"...? Thanx in adavance to anybody willing to throw me a bone :D

---

### Post by Smandola on 2006-07-29
z33, 

I doubt you will find a book.  But most everything you need to do can be found in the forums.  The How-To forums are great. [http://ubuntuforums.org/forumdisplay.php?f=100](http://ubuntuforums.org/forumdisplay.php?f=100)

I have been able to find answers to most of my questions either using the How-To, or by reviewing/searching for posts in the Ubnuntuforums.org   

I don't want to promote the use of other forums in this forum, but I will also use Linux Questions ([http://www.linuxquestions.org/](http://www.linuxquestions.org/)) to find additional information.  Keep in mind the posts may not be specific to Ubuntu.  

This probably doesn't help you much, but if you have a specific question, reply to the post and I'm sure you will get a response.  

Good Luck.
s. 

btw-> that is one hillarious picture !

---

### Post by z33k3r on 2006-08-01
Yeah, that is great advice that I hear a lot of. I as a tech support employee know that all to well. I was just wondering if there is a place I could go to for a quick run through of after Ubuntu Server is installed, how to administrate it with common examples and situations. You know, for M$ power user looking for a quick tutorial on how to be a linux server admin with out all the grunt work of learning every detail and what it's history is ;) I will keep looking...

---

### Post by z33k3r on 2006-08-01
I accually found something usefull! (not that anything here isn't, i accually had to fix my dns and found /etc/rsolv.conf here ;) )

[http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

### Post by adamkane on 2006-08-01
For those that want Gnome/KDE and LAMP see below. Very straightforward.

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start apache and mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by z33k3r on 2006-08-01
Thanks adamkane, but I already have Ubuntu Server with LAMP istalled, I am looking for ways to administrate the system the easiest. Working with Webmin right now...trying to figure out DNS, users, and how to work Apache :)

---

### Post by stanz on 2006-08-01
[FONT=Comic Sans MS][SIZE=2]> **z33k3r said:**
> I am looking for ways to administrate the system the easiest. Working with Webmin right now...trying to figure out DNS, users, and how to work Apache :)
Like me [Dummy Too], we're in for allot of reading.
[/SIZE][/FONT] [LEFT][FONT=Comic Sans MS][SIZE=2] I checked out that 'howtoforge' page also...I'm thankful things like that [/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]can be found![/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2][Ubuntu help]("https://help.ubuntu.com/community/WebServerHosting?")[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2][Ubuntu LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP")[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2][Ubuntu Server Guide]("https://help.ubuntu.com/ubuntu/serverguide/C/index.html")[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2][Apache Site]("http://httpd.apache.org/")[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2][Linux Server]("http://www.linuxforums.org/servers/setting_up_a_server.html")[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2] ...are afew of what I'm reading.[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2] Some O'Reilly Articles:[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT] [FONT=Comic Sans MS][SIZE=2][The Basics of DNSSEC ]("http://www.onlamp.com/pub/a/onlamp/2004/10/14/dnssec.html")[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]
[/SIZE][/FONT]       [FONT=Comic Sans MS][SIZE=2][Understanding Zeroconf and Multicast DNS]("http://www.oreillynet.com/pub/a/wireless/2002/12/20/zeroconf.html")[/SIZE][/FONT][FONT=Comic Sans MS][SIZE=2]

**To add a book, to have 'on-hand'... The Debian GNU/Linux Bible**
[/SIZE][/FONT]  [FONT=Comic Sans MS][SIZE=2] Any Help to ya?   :-\" [/SIZE][/FONT]
[/LEFT]

---

### Post by adamkane on 2006-08-02
There are people with a lot more experience than me, but the main tools you need are phpmyadmin and cron.

phpmyadmin - Browse your database and administer users.

cron - Backup your database (.sql file) to a safe place. Import when necessary using phpmyadmin.

---

### Post by natrixgli on 2006-08-07
Just curious, what does the above mentioned have on Webmin? 

-Cheerio, n8

---

### Post by Gtaylor on 2006-08-07
They don't really have anything "on" webmin, as they are used for different things:

phpmyadmin: Good for administering MySQL servers and databases.
crontab: A task scheduler for executing shell-side events at predetermined times.
webmin: A generic web-based server administration application.

So they're really meant for different things and fill different niches.

---

### Post by chrisfay on 2006-08-07
Webmin has a full featured backup utility for local or remote scheduled backup as well. Not to mention a backup utility for the modules within webmin so you don't have to reconfigure it if something goes wrong.

---

### Post by natrixgli on 2006-08-08
Dare I suggest that dummies shouldn't admin servers? lol... [-X

---

