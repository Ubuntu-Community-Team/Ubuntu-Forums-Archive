---
title: "How to start/stop service with Apache"
date: 2012-10-24
forum: Server Platforms
---

### Post by Juggler00 on 2012-10-24
Banging my head against a wall... I'm trying to find a way to do the following:

Using Apache, I'd like to be able to start and stop a service on the same server. Essentially, I'm looking for a way to allow Apache (or some script called by Apache) to call "sudo service XXXX start". 

I realize there are severe security implimications with this, and I'm looking to minimize the possible effects. There is only a single service that I need to do this for. I've seen some solutions that involve "hacking" the setuid (C/Perl wrapper), others involved editing the sudoers file. 

Is there a better way? 

many thanks,
   J.

---

### Post by Juggler00 on 2012-10-24
Here was the easy answer:

To the sudoers file, add the following line:
www-data ALL=(ALL) NOPASSWD: /etc/init.d/theinitscript

---

