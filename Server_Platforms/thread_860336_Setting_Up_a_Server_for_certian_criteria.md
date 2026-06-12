---
title: "Setting Up a Server for certian criteria"
date: 2008-07-15
forum: Server Platforms
---

### Post by Sbwarren21 on 2008-07-15
I am fairly new Ubuntu and I am wanting to start a home server for approx. 50 people can access.  I have a few questions to make sure ubuntu can fit my needs and how easy it is to set up.  My criteria are as follows:

Must provide FTP support.
Be able to host a forum.
Be able to manage users with different user names, passwords and be able to track their usage.

I do not care able power usage and have unlimited internet bandwidth.

Thanks,
Sbwarren

---

### Post by Peter Anselmo on 2008-07-15
Ubuntu Server should fit the bill just fine.  I have it on a home server with a similar use case.

For FTP:  I'm using vsftpd, and it fits the bill.  It's easy to download and install using apt-get.  The Ubuntu server documentation has as write up about it [here]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html").

For a forum:  If you expect a lot of traffic and posts, I'd suggest going the web-based route.  This means you'll need to install apache, php and mysql.  Those are also covered in the docs [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html"), [here]("https://help.ubuntu.com/8.04/serverguide/C/php5.html") and [here]("https://help.ubuntu.com/8.04/serverguide/C/mysql.html").  Once you have those up, you can use phpBB, drupal, or whatever other forum software you want.

You'd be able to manage users easily, but the downside of the above suggestions is that the forum users will be different from the local system users.  I suppose you could create a script to sync the two, but I'm not sure how good you are with shell scripts.

---

### Post by wepalm on 2008-07-15
> **Sbwarren21 said:**
> 
Be able to host a forum.
Be able to manage users with different user names, passwords and be able to track their usage.


What do you want the forum to do?  normal phpBB forum or like imageboard or something?

---

### Post by Sbwarren21 on 2008-07-15
> **wepalm said:**
> What do you want the forum to do?  normal phpBB forum or like imageboard or something?

I want to be able to have a normal discussion board with picture support.  Something along that line.

---

### Post by Sbwarren21 on 2008-07-15
> **Peter Anselmo said:**
> Ubuntu Server should fit the bill just fine.  I have it on a home server with a similar use case.

For FTP:  I'm using vsftpd, and it fits the bill.  It's easy to download and install using apt-get.  The Ubuntu server documentation has as write up about it [here]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html").

For a forum:  If you expect a lot of traffic and posts, I'd suggest going the web-based route.  This means you'll need to install apache, php and mysql.  Those are also covered in the docs [here]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html"), [here]("https://help.ubuntu.com/8.04/serverguide/C/php5.html") and [here]("https://help.ubuntu.com/8.04/serverguide/C/mysql.html").  Once you have those up, you can use phpBB, drupal, or whatever other forum software you want.

You'd be able to manage users easily, but the downside of the above suggestions is that the forum users will be different from the local system users.  I suppose you could create a script to sync the two, but I'm not sure how good you are with shell scripts.



Thanks for your help!

---

### Post by Sbwarren21 on 2008-07-15
Let me ask.  Would the 6.06.2 version work for all these.  The reason I ask is that I have an old G4 just lying around that I could use and this is the latest version that would work.  I was going to get a 300 dollar dell and use it but if it works on MAC then that would be cheaper. Any suggestions?

---

### Post by windependence on 2008-07-16
That should work just fine. I ran a forum on an old AMD K6-2 system for years with 500 users. 

I would recommend simple machines forum with tinyportal over phpBB unless you like deleting spammers all the time. I migrated from pgpBB years ago and I am very satisfied with simple machines.

-Tim

---

