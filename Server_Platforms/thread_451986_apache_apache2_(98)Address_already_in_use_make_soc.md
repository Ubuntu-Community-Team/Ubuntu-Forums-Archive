---
title: "apache apache2 (98)Address already in use: make_sock: could not bind to address"
date: 2007-05-22
forum: Server Platforms
---

### Post by dogatemycomputer on 2007-05-22
I thought I would just post a short note in case someone else ever experiences this problem.  I recently installed apache2 with ssl and mysql.  I'm still a noob so I do some stupid stuff every once in a while but i'm learning. 

After installing apache, mysql and openssl I start seeing these errors when trying to launch apache:

```
rwalkerd@opswalkerd1:/var/www# /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue May 22 18:26:38 2007] [warn] NameVirtualHost *:443 has no VirtualHosts
[Tue May 22 18:26:38 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
**httpd (no pid file) not running**
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue May 22 18:26:48 2007] [warn] NameVirtualHost *:443 has no VirtualHosts
[Tue May 22 18:26:48 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
**(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443**
**no listening sockets available, shutting down**
Unable to open logs
```


The errors indicating the httpd (http daemon) couldn't start was caused by a duplicate entry in /etc/apache2/ports.conf:

```
walkerd@opswalkerd1:/etc/apache2/sites-available$ more /etc/apache2/ports.conf
Listen 80
Listen 443

Listen 443
```

Needless to say removing the 3rd and 4th line above (the space and the second "listening" entry) resolved the problem. Once these entries were removed I was able to restart the apache2 service:

```
walkerd@opswalkerd1:/etc/apache2/sites-available$ sudo /etc/init.d/apache2 force-reload
 * Forcing reload of web server (apache2)...                                                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue May 22 18:49:50 2007] [warn] NameVirtualHost *:443 has no VirtualHosts
[Tue May 22 18:49:50 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Tue May 22 18:50:00 2007] [warn] NameVirtualHost *:443 has no VirtualHosts
[Tue May 22 18:50:00 2007] [warn] NameVirtualHost *:80 has no VirtualHosts
```

Hopefully this helps save someone else the trouble of tracking this issue down.

Have a great day!

---

### Post by Romanmir on 2007-06-10
I'm having the same behavior, but I only have ```
Listen 80
``` in my posts.conf.

I have LAMP and openSSL installed. I notice that my apache dies occasionally, and I can't seem to figure out why, but I get the same error message when I try to restart the service..

Any other ideas?

---

### Post by Bionic_Beefpile on 2007-06-14
I was getting conflicts between Apache and Apache2.  I just used Synaptic to uninstall Apache, and everything fixed itself.

---

### Post by Romanmir on 2007-06-19
hmm..

After after seeing the error again, I ran an `lsof | grep apache` to see what exactly was keeping those logs open. It seems that python is the culprit.

A few weeks ago I set up a cron job that was supposed to pause my bittorrents. It did this by sending a SIGSTOP to the all python processes.

Thus, after all the python processes are sent the SIGCONT, apache seems to fire right up..

My question then would be why does python need to/ end up holding open those files??

I am running cacti as well, but that uses php, as far as I know. I'm also running Gallery2, but once again, php, not python is in play..

---

### Post by dbrooke on 2007-10-24
> **Bionic_Beefpile said:**
> I was getting conflicts between Apache and Apache2.  I just used Synaptic to uninstall Apache, and everything fixed itself.


Hmmm, I'm getting this to:
 * Starting web server apache2
(98)Address already in use: make_sock: could not bind to address [::]:443
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:443
no listening sockets available, shutting down
Unable to open logs
   ...fail!
-----------------------------

You mentioned apache... this seemed to happen after I installed ISPConfig.. which compiles a separate apache... wonder if that is causing conflicts?

Donovan

---

### Post by dbrooke on 2007-10-24
solved this error... there was more than one ports.conf file.

apache2>ports.conf
apache2>sites-enabled>ports.conf
both had "LISTEN" entries.

Now on to my other ssl issues! :)

Donovan

---

### Post by Meethoss on 2008-04-08
dbrooke - I know it was a while ago you posted this but I just had the exact same problem. Thanks for helping me solve it! :)

---

### Post by jdogzilla on 2008-06-28
Hello, I am still having this problem ... single ports.conf file, same message when I try to start apache server

 * Starting web server apache2
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!

Any other suggestions?

---

### Post by kustomjs on 2008-07-13
i am getting the same error message does anybody know how to fix this?

---

