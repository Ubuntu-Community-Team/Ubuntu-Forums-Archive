---
title: "Apache aliases not working after upgrade (permissions issue on home folder)"
date: 2013-10-28
forum: Server Platforms
---

### Post by Maheriano on 2013-10-28
I upgraded my desktop and laptop to Ubuntu 13.10 and now I can't access my development site anymore for a website I'm working on. I have Apache installed on both machines and both of them are giving me forbidden errors when I try and access them. Here are the specifics:

I have port 8001 on my switch forwarded to port 80 on this machine. When I visit this IP in my browser ([http://my.ip.xx.xx:8001](http://my.ip.xx.xx:8001)) I get the default Apache page:
```
It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.
```
So Apache is working and has access to the /var/www directory where these files are stored. I'm running my development site out of my home directory, /home/deemar/NetBeansProjects/mywebsitename.com.
Here is my alias setup:
```
Alias /mywebsitename /home/deemar/NetBeansProjects/mywebsitename.com
<Directory /home/deemar/NetBeansProjects/mywebsitename.com>
Order allow,deny
Allow from all
</Directory>

```
And that configuration file is located in /etc/apache2/conf.d/mywebsitename.conf
Here are the permissions on my folder:
```
drwxr-xr-x 10 www-data deemar  4096 Oct 25 23:36 mywebsitename.com
```
As you can see, the owner of this folder is www-data which, as I just discovered, is a group which doesn't exist on my machine:
```
deemar@Chugger:~/NetBeansProjects$ groups 
deemar adm dialout cdrom sudo dip plugdev lpadmin sambashare
```
I've tried this with ownership as my user as well, doesn't work either way. When I try and access my website at [http://my.ip.xx.xx:8001/mywebsitename/](http://my.ip.xx.xx:8001/mywebsitename/) I get the following:
```
Forbidden

You don't have permission to access /mywebsitename/ on this server.

Apache/2.4.6 (Ubuntu) Server at my.ip.xx.xx Port 8001
```

What's going on here?

---

### Post by TheFu on 2013-10-28
TL;DR Sorry.

Did you realize that apache v2.4 is now used, not v2.2?
[https://httpd.apache.org/docs/2.4/](https://httpd.apache.org/docs/2.4/) might be helpful.
I'd probably start looking for an answer by googleing "apache 2.2 vs 2.4"
* [https://httpd.apache.org/docs/current/upgrading.html](https://httpd.apache.org/docs/current/upgrading.html) was found.

---

### Post by pqwoerituytrueiwoq on 2013-10-28
```
Order allow,deny
Allow from all
```
has been placed with
```
Require all granted
```

---

### Post by Maheriano on 2013-10-28
> **pqwoerituytrueiwoq said:**
> ```
Order allow,deny
Allow from all
```
has been placed with
```
Require all granted
```

Thank you, I also had to move my mywebsite.conf file from /etc/apache2/conf.d into /etc/apache2/sites-enabled and then it worked no problem. Thanks, problem solved.

---

