---
title: "How to set Postfix smtp authentication ?"
date: 2010-08-11
forum: Server Platforms
---

### Post by solidussnake on 2010-08-11
I have built up my mail server successfully,
can send(smtp) and receive(POP and IMAP) with my domain.
Howver, I want my smtp to be authenticated by username and password.

[IMG]http://i171.photobucket.com/albums/u312/solidussnakex/Untitled-1.gif[/IMG]

Now I can connect to my smtp without any anthenication(as below).
But I want it to check username and password(as above).

[IMG]http://i171.photobucket.com/albums/u312/solidussnakex/Untitled-2.gif[/IMG]



Here are the setting I made after a fresh ubuntu 10.04 installation.

sudo useradd [my_name]
sudo passwd [my_name]
dig mx [mydomain.com]
sudo apt-get install postfix
sudo apt-get install mailutils
sudo postconf -e "home_mailbox = Maildir/"
sudo postconf -e "mydestination = localhost.localdomain, localhost, [mydomain.com]"
sudo postconf -e "mynetworks = 127.0.0.0/8, 192.168.1.0/24"
sudo postconf -e "inet_interfaces = all"
sudo postconf -e "inet_protocols = all"
sudo  /etc/init.d/postfix stop
sudo  /etc/init.d/postfix start

set godaddy domain directed to [my IP]
set router port fowarding at port 25, 110, 143 to my server


What should I do next ?

---

### Post by HermanAB on 2010-08-11
Howdy,

You need smtp-auth.  Go to the Postfix project web site and start reading.

Otherwise, install Citadel.  It does everything and it installs in about 20 minutes.

IMHO Postfix is a big waste of time, unless maybe if you have more than 30,000 users.

---

### Post by solidussnake on 2010-08-11
> **HermanAB said:**
> Howdy,

You need smtp-auth.  Go to the Postfix project web site and start reading.

Otherwise, install Citadel.  It does everything and it installs in about 20 minutes.

IMHO Postfix is a big waste of time, unless maybe if you have more than 30,000 users.

[https://help.ubuntu.com/10.04/serverguide/C/postfix.html](https://help.ubuntu.com/10.04/serverguide/C/postfix.html)
I have read through this,
it only mentioned something related to certificate,
but nothing about the password.
In fact I don't need any cert, only want a login & password.


For the Citadel, it's good, will try later.

---

### Post by HermanAB on 2010-08-12
OK, that guide is good for the configuration of smtp-auth.  You got to do that first.  It provides a secure channel for password authentication.

Then, the username and password authentication itself can be done in one of two ways:  Either make a standard user account for each user and let PAM handle it, or install MySQL and configure that to handle the users and passwords.

As you can see, setting up all the features one needs for a full featured mail system with Postfix, is a non-trivial problem that can lead to several weeks of happy man page reading and debugging.  In contrast, Citadel sets it all up in a few minutes.  That is why I gave up with Postfix many years ago already.  

Granted, Postfix is better than the prehistoric Sendmail, but it is very 20th century...

---

