---
title: "mime.types randomly disappeared from apache2?"
date: 2009-05-01
forum: Server Platforms
---

### Post by Afisamuleal on 2009-05-01
Hey, I've been running a server for five years. The hardware is old and outdated so it hasn't been updated recently, and because of hardware failure, it's unlikely I'm able to update it (certainly apt doesn't work any more, this is not my issue).

Today, I was playing around and enabled the cgi in non-cgi-bin directories. I restarted the server, and suddenly my directory listings had no images and all .?? files began showing up (.htaccess, etc)... and I had no idea what was going on.

It appears from the log there is no mime.types configuration, now. I didn't change anything! I changed the one line, so I didn't think to make a backup. I have absolutely nothing with the word mime in the /etc/apache2 folder except mime_magic.conf in the mods-available folder. There is no line anywhere in any of my config files about mime.types, why haven't I gotten an error before??

I found a mime.types file, I guess, from a site, and put it in a newly created /etc/apache2/conf directory and changed my 0 non-commented-out lines httpd.conf file (everything is in apache2.conf) to contain TypesConfig conf/mime.types and /etc/apache2/conf/mime.types. Still nothing.

See example:
[http://sam.ashensky.com/](http://sam.ashensky.com/)

but
[http://ashensky.com/](http://ashensky.com/)
uses the htaccess redirect fine, and authentication still works.
What's the deal!

[http://www.be.telge.us/e/img/](http://www.be.telge.us/e/img/)
hasn't got my header:
[http://www.be.telge.us/e/img/HEADER.html](http://www.be.telge.us/e/img/HEADER.html)

I don't understand... any help?

---

### Post by windependence on 2009-05-02
I can't reach any of them.

-Tim

---

### Post by Afisamuleal on 2009-05-02
right! sorry not to update.

In order to fix this problem I made a backup of my config files and copied the files off of my locally configured laptop. I played around with some stuff and couldn't manage to fix the problem with a complete new set of working configuration files.

Since that's so crazy and confusing, I bought a big harddrive and am rsyncing the directories onto it. I hope I don't have mysql incompatibility issues like last time I backed up my server.

If it's any food for thought, I had uncommented the line allowing cgi to execute anywhere; might a malicious script have been run in the seconds before I recommented it? My sever had pretty lax security, but I can't imagine how a mime.types file of default permissions could've been compromised...

---

