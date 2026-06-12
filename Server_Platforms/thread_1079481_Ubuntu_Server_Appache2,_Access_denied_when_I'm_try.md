---
title: "Ubuntu Server Appache2, Access denied when I'm trying to access a file"
date: 2009-02-24
forum: Server Platforms
---

### Post by EizoSiege on 2009-02-24
Hi, I'm experimenting with an Ubuntu Server and have got it up and running. Addresse to the server: [http://80.213.167.52/siegeftp/](http://80.213.167.52/siegeftp/)

The problem is that when I try to access a file I get this: 
"[I]Forbidden

You don't have permission to access /siegeftp/Alarm.rar on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch Server at 80.213.169.241 Port 80[/I]"

Anyone who know how I can fix this?


Thanks in advance for all replies

---

### Post by volkswagner on 2009-02-24
Apache2 files that you want access to via the web should have group set to www-data.  You will need to read up on security and permissions to fit your needs.

You may want to read up on virtual hosts.  This is the easiest way to set up web sites.

Places for info:
[Ubuntu Server Guide]("http://doc.ubuntu.com/ubuntu/serverguide/C/")

Particularly [Apache2]("http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html")

---

### Post by EizoSiege on 2009-02-24
I didn't quite get what you where saying but is Chmod probobly the thing I am looking for? 
As you can see if you clik on the link to my server you get a big FORBIDDEN header which I want to go away.

Still thanks for the reply

---

### Post by terazen on 2009-02-24
Anything in your apache logfile?  It's /var/log/apache2/error.log and /var/log/apache2/access.log usually I think.

Also, there should be a default configfile in /etc/apache2/sites-available called default or 000-default.  Whatever folder that file says is your web folder just make sure www-data can get to it.

---

