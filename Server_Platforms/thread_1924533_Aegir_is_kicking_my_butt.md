---
title: "Aegir is kicking my butt"
date: 2012-02-12
forum: Server Platforms
---

### Post by antiacus on 2012-02-12
I'm hung up on this problem for about three weeks now.  I'm wanting to use Aegir for my drupal multi-site platform and i can't seem to figure out what i'm doing wrong.  

This is the error i'm getting after trying to install hostmaster:

[PHP]Do you really want to proceed with the install (y/n): y
SQLSTATE[HY000] [2002] Can't connect to local MySQL server through   [error]
socket '/var/run/mysqld/mysqld.sock' (2)
Unable to connect to database server.                                [error]
apache on localhost could not be restarted. Changes might not be     [warning]
available until this has been done. (error: apache2: Could not
reliably determine the server's fully qualified domain name, using
blablabla.localhost for ServerName[/PHP]I think i've done everything correctly.  I have mysql & apache running via xampp stack. 

Anything obvious stand out?  Is there a better place to ask this question?

So far i've not been able to set up a static-ip, could this be my problem?  I tried following the steps in this video:
[http://www.youtube.com/watch?v=ClMeY7xKEAU](http://www.youtube.com/watch?v=ClMeY7xKEAU)

When i get to the part where i'm supposed to add an ip address (1:33 in the video) i put in 127.0.0.1
Also, i wasnt' sure what to put for my DNS, perhaps i fouled that up.

Thanks for any suggestions or help.

---

