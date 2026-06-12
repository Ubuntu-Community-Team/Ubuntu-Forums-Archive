---
title: "Default permissions on /var/www/ ??"
date: 2007-08-31
forum: Server Platforms
---

### Post by kpm on 2007-08-31
Hi, dumb question but...
I am setting up a LAMP server and followed a few steps from a website.  Part of the instructions were to chmod /var/www to the user name so one would not have to sudo every command in /www. After doing so I then recalled that the www-data user (the Apache user) was needed for some web applications (if I remebered correctly)... Anyway, I would like to set the owenership back to Ubuntu canned LAMP server install default, but I never checked what it was before I made the change... is my assumption that www-data is the owner of /var/www correct??

Thanks

---

### Post by aysiu on 2007-08-31
root is probably the original owner.

---

### Post by kpm on 2007-08-31
Thanks. I'll switch back to that and chown to www-data as need be.

---

