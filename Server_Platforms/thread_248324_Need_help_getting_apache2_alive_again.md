---
title: "Need help getting apache2 alive again"
date: 2006-08-31
forum: Server Platforms
---

### Post by braddcadd on 2006-08-31
Somewhere in the course of installing embperl and phppgadmin, apache died.  I can;t figure out how to get it up and running again.  Here is some info to help diagnose:

My hosts file:
```

127.0.0.1 localhost UbuntuTop
127.0.1.1 UbuntuTop

```

Last few lines of my log file:
```

[error] [client 127.0.0.1] File does not exist: /htdocs
[error] [client 127.0.0.1] File does not exist: /htdocs
[notice] caught SIGTERM, shutting down
[notice] Apache/2.0.55 (Ubuntu) Embperl/2.0.1 mod_perl/2.0.2 Perl/v5.8.7 configured -- resuming normal operations
[error] [client 127.0.0.1] File does not exist: /htdocs
[error] [client 127.0.0.1] File does not exist: /htdocs
[error] [client 127.0.0.1] File does not exist: /htdocs
[error] [client 127.0.0.1] File does not exist: /htdocs

```

Error given when I try to restart the webserever:
```

braddcadd@UbuntuTop:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... grep: /etc/apache2/sites-enabled/[^.#]*: No such file or directory
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

```

Here is my version info:
```

Server version: Apache/2.0.55
Server built:   Jul 26 2006 17:59:52

```

Can anyone help with this issue?  Thanks.

---

### Post by kidders on 2006-08-31
Ergh, oh dear...

The default website and apache config files seem to have gone missing, although I imagine you can probably see that for yourself :(

What (if anything) is left in your /etc/apache2?

Depending on how much you know about apache, you might be able to pull out the bits of your config files that are triggering the errors you mentioned and post them, maybe.

---

### Post by chrisfay on 2006-08-31
> apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

This can be fixed by adding the ServerName option in apache2.conf:
```
ServerName "domain.name.tld"
``` 
(replacing "domain.name.tld" with the fqdn of your server)

The other stuff seems more serious. You may have removed some of the files Apache2 needs to run/access such as the sites-enabled folder.

Have you tried to purge remove and reinstall?

```
sudo apt-get --purge remove apache2
sudo apt-get install apache2

or

sudo apt-get --purge remove apache2-common
sudo apt-get install apache2-common
```

---

### Post by braddcadd on 2006-09-01
Thanks. The purge / reinstall did it.

Webserver IS ALIVE!

---

### Post by SubWolf on 2007-06-20
This is gonna drive me nuts. :)

[Wed Jun 20 19:45:23 2007] [error] [client 127.0.0.1] File does not exist: /htdocs
[Wed Jun 20 19:48:32 2007] [error] [client 127.0.0.1] File does not exist: /htdocs

Worked fine before the feisty upgrade. Tried the purge/re-install, no dice.

rgrep in /etc/apache2 for 'htdocs' returns zero results.

Any ideas? I'm stumped.

Note: This is while trying to reach any site enabled on my local box, /htdocs really does not exist, the DocumentRoot for the default is /var/www/subwolf.bgn.org/ - which is being ignored.

---

### Post by kidders on 2007-06-21
Hi there,

Could you post your default server's configuration? I suspect there's a typo in it ... "/htdocs" may be a default value (which would explain why it isn't explicitly mentioned anywhere).

---

### Post by vanderkerkoff on 2008-03-12
Did anyone get a resolution for this?

I'm getting exactly the same error in my error.log and it's also drving me nuts

---

