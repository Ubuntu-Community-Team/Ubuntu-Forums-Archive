---
title: "Apache2 config issues?"
date: 2011-09-22
forum: Server Platforms
---

### Post by mace9984 on 2011-09-22
I'm having some issues configuring a new lamp server.  When I navigate to localhost I get 

[CENTER]"Not Found

The requested URL / was not found on this server."[/CENTER]

I have phpmyadmin installed, and I can successfully navigate to that using localhost/phpmyadmin.  I think I'm missing something in the config files or something. 

I was hoping that one of you may be able to point me in the right direction.  I am running another web server from this location but they are both assigned to different ports.

I've tried everything I could google to no benefit.

---

### Post by Beacon11 on 2011-09-22
Well... are you visiting the right port?

---

### Post by mace9984 on 2011-09-22
I'd say yeah because I'm seeing the server, just not the test document on the server.

---

### Post by mace9984 on 2011-09-23
Anyone?

---

### Post by Ryan Dwyer on 2011-09-23
Check Apache's error log to see what's going on (/var/log/apache/error.log). You might have a misconfigured DocumentRoot or the www-data user might not be able to read those files.

---

