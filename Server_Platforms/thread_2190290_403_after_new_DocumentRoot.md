---
title: "403 after new DocumentRoot"
date: 2013-11-26
forum: Server Platforms
---

### Post by george15 on 2013-11-26
I am a somewhat new to ubutnu. I've looked for the answer before posting here, but found nothing helpfull. 
Sorry in advance if I missed something abvious.
I installed ubuntu 13.10 server ( ip address 192.168.1.103 )
  When I went to 192.168.1.103 in the browser I got:
--------------------------------------------
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
--------------------------------------------

Then I modified 000-default.conf from
             DocumentRoot /var/www
to
             DocumentRoot /home/me/www

Now in the browser I am getting 403 :
Forbidden

You don't have permission to access / on this server.
Apache/2.4.6 (Ubuntu) Server at 192.168.1.103 Port 80

Why is moving doc root gives permission error?

---

### Post by drmrgd on 2013-11-26
I don't know a ton about apache, but  the file that I thought should be edited is in /etc/apache2/sites-available/default.  If that's indeed the file you changed, did you make sure to change both the 'DocumentRoot' line **and** the 'Directory' lines?  As a quick test, I just did what you tried and it seemed to work OK.

**EDIT** One more thing that I forgot to say, I think by default, the directory should be owned by 'www-data'.  You might also try changing ownership of the directory.

---

### Post by george15 on 2013-11-26
In ubuntu 13.10 default became 000-default.conf
I do not see Directory lines in there.
I did not think permissions mattered since the directory has world read permission.
Either way adding www-data access did not change anything.

---

### Post by nerdtron on 2013-11-27
The directory has world read permission - yes, but how about the upper folders?
Be sure to have 755 on the folders and parent folder of the directory you want to use. Access 403 is permission issues.

---

### Post by sandyd on 2013-11-27
> **george15 said:**
> In ubuntu 13.10 default became 000-default.conf
I do not see Directory lines in there.
I did not think permissions mattered since the directory has world read permission.
Either way adding www-data access did not change anything.

hope it has passthrough permissions

btw, try this
```

su www-data
bash
cd /

```
now, start navigating one level at a time, until you get permission denied error.
Fix the permissions on that folder, and you should be fine

Also, make sure you have an index file - directory listings are disabled by default and will result in an error as well.

---

