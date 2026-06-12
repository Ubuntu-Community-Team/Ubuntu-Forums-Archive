---
title: "Private-public webserver"
date: 2012-08-05
forum: Security
---

### Post by dakkerd on 2012-08-05
Hi all,

I've been working on an Ubuntu server, chiefly as a NAS. Works fine, yet I want to go to the next level.

Goal is to check my webcam streams (using motion), complete my dokuwiki (used as sort of a tool to remember how I all configured it, obviously without listing pass and keys), have a ftp for a very limited number of people. 

I connect using SSH, and I would like to have this private webserver so I can indeed run my dokuwiki or other stuff. Basically, to 'quickly' access some of the key elements either through a webbrowser, either through ftp. 

Hence, I would like to have a webserver of which I'm rather confident that it's secure (and that they cannot hack the ubuntu streams...). I'm not interested in setting up a website publically available to anyone who wants to. Only me and some others (max 10). 

Is there a very secure way of setting up a webserver. Much like you setup x11vnc accepting only localhost. In other words, can I setup a server so that one has to have a ssh key before actually reading a website or watching a stream? In other words, can I install a private server accessible through a webbrowser?

---

### Post by samiux on 2012-08-05
> **dakkerd said:**
> Hi all,

I've been working on an Ubuntu server, chiefly as a NAS. Works fine, yet I want to go to the next level.

Goal is to check my webcam streams (using motion), complete my dokuwiki (used as sort of a tool to remember how I all configured it, obviously without listing pass and keys), have a ftp for a very limited number of people. 

I connect using SSH, and I would like to have this private webserver so I can indeed run my dokuwiki or other stuff. Basically, to 'quickly' access some of the key elements either through a webbrowser, either through ftp. 

Hence, I would like to have a webserver of which I'm rather confident that it's secure (and that they cannot hack the ubuntu streams...). I'm not interested in setting up a website publically available to anyone who wants to. Only me and some others (max 10). 

Is there a very secure way of setting up a webserver. Much like you setup x11vnc accepting only localhost. In other words, can I setup a server so that one has to have a ssh key before actually reading a website or watching a stream? In other words, can I install a private server accessible through a webbrowser?

[Hiawatha]("http://www.hiawatha-webserver.org/") is a fast, lightweight and sercue web server.  You can refer this [HOWTO]("http://secure-ubuntu-server.blogspot.com/").

Samiux

---

### Post by spynappels on 2012-08-06
You can use an ssh tunnel and access the webserver through that. It would mean you do not need to open port 80 to the world by means of port-forwarding on your router, but anyone you have given ssh access too will be able to tunnel requests to the web server through that. Secure SSH with keys though, it makes it easier to revoke access by deleting a user's key from the authorized keys file.

---

