---
title: "Ubuntu Server for multiple tasks"
date: 2006-06-09
forum: Server Platforms
---

### Post by jitesh on 2006-06-09
I want to have a server running multiple tasks, firstly as my PostgreSql database server, but also as a print and file sharing server. Is this possible? Is it advisable?  Where do I begin with this?

---

### Post by tribaal on 2006-06-09
Yes sure! It's even pretty easy to do (I'm not sure about the printing though).

For the filesharing: If you wish to share files to a Windows network you need to install a Samba server (samba is what makes the "interface" with windows networks).

```
sudo apt-get install samba
```

Samba also handles the printing, but I never go into that personally, so I couldn't really help you on that. I'm sure there are plenty of ressources on the web for that, though. Try [the wiki]("https://wiki.ubuntu.com/") first, it's a good start.

For the Postgres DB, I guess the database itself is a server (a software server), like mySQL. So basically it's already set up, if you have it up and running. I'm not really used to Postgres though.

Hope this helps...

- trib'

---

### Post by jitesh on 2006-06-09
Thanks. All the network machines are Linux based, so how do I setup a network like this?

---

### Post by Iowan on 2006-06-09
[http://www.howtoforge.com/]("http://www.howtoforge.com/")
Here's another good site.  There are articles for setting up Samba, or using Ubuntu as an ISP (Apache,SQL, etc) for either Breezy or Dapper.

---

