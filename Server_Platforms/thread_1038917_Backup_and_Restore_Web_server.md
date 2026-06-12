---
title: "Backup and Restore Web server"
date: 2009-01-14
forum: Server Platforms
---

### Post by prowebber on 2009-01-14
Hello all.

I am looking for the most reliable and quickest way to backup a ubuntu webserver and restore it. 

I'd like to hear what others have experience with this?

-Thanks.

---

### Post by Traumadog on 2009-01-14
I've been using a 1TB external USB drive, rsync, and a simple BASH script to perform automated backups of all of my data including my web server.  The process is simple, inexpensive, and reliable.  The only thing you may need to purchase is the drive you wish to use as your backup, and rsync should be available to you as part of you Ubuntu package.

I've had to restore my web server information from the backup once since I started using this system, and the restore process was simple and quick.  If you are interested, I can post the script I'm using here, or you can search for a similar here on the forum  (There are several here, I think). I'm sure with just a few simple modifications, the script will work well for you.

Hope this helps. :)

Best wishes,

Traumadog.

> **prowebber said:**
> Hello all.

I am looking for the most reliable and quickest way to backup a ubuntu webserver and restore it. 

I'd like to hear what others have experience with this?

-Thanks.

---

### Post by R.Bucky on 2009-01-14
I use Webmin, which installs nicely using a .deb package. I send all of my data (e.g. databases, apache/php config files, and web server directory) to a 1TB external as well. I also use the software to backup my regualr files as well. Ideally, I would like to have a 200MB or so flash drive so that the external does not have to spool up every night, but hey!

Webmin does a great job at managing my backups. No complaints here/

---

