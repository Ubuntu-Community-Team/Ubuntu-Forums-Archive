---
title: "Server Network Configuration Broken? - Will only listen/bind on one port? Please Help"
date: 2013-11-27
forum: Server Platforms
---

### Post by kenetik on 2013-11-27
Pre Reqs/Useful:
```

(This is a web/dedicated server)
Distributor ID: Ubuntu
Description:    Ubuntu 13.04
Release:        13.04
Codename:       raring

Hardware: ProLiant DL160G5p

```
*Pastes: Apache vhost configs: [http://paste.ubuntu.com/6486692/](http://paste.ubuntu.com/6486692/) & [http://paste.ubuntu.com/6486707/](http://paste.ubuntu.com/6486707/)*

**Issue: Can't listen/bind to any port other than 80.** :confused:

The server has some prior configurations (non default) set on it. It seems that I can't get anything to bind/listen on a port other than 80. For example, I've got apache serving the same document (/var/www/index.html) on port 80 and 90 (two separate and enabled vhost configurations - see the pastes at the beginning of this thread for copies of the configs). Starting apache doesn't throw any errors.

```

root@beast:/etc/apache2/sites-available# a2ensite default
Site default already enabled
root@beast:/etc/apache2/sites-available# a2ensite default90 
Site default90 already enabled
root@beast:/etc/apache2/sites-available# service apache2 start
 * Starting web server apache2                                               [ OK ]

```

Thus, no typical "cant bind to :::90". The server/apache aren't logging any errors (that I can find?) however I can only connect/serve from port 80. 

```

root@beast:/var/log/apache2# cat error.log 
[Wed Nov 27 13:52:33 2013] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations

```

Firewalls are disabled for testing purposes:
```

root@beast:/etc/ufw# ufw status
Status: inactive
root@beast:/etc/ufw# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

Output from lsof: 
```

root@beast:/etc/ufw# lsof -i
COMMAND   PID       USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
[...]unnecessary sshd listings [...]
apache2 27566       root    4u  IPv6 260215      0t0  TCP *:http (LISTEN)
apache2 27571   www-data    4u  IPv6 260215      0t0  TCP *:http (LISTEN)
apache2 27572   www-data    4u  IPv6 260215      0t0  TCP *:http (LISTEN)

```
*Does it seem odd that it's only mentioning/listening on IPv6?*


What am I missing? What am I overlooking? 

I appreciate your time and willingness to help, any guidance or suggestions are very much appreciated!

---

### Post by Doug S on 2013-11-28
You don't mention the file /etc/apache2/ports.conf. You need to make a change in it also.```
doug@s15:/etc/apache2$
doug@s15:/etc/apache2$ [COLOR=#ff0000]sudo lsof -i -P | grep apache[/COLOR]  [COLOR=#ff0000]<<< With the default ports.conf file[/COLOR]
apache2   2303            root    3u  IPv4  15028      0t0  TCP *:80 (LISTEN)
apache2   2303            root    4u  IPv4  15031      0t0  TCP *:443 (LISTEN)
apache2   2413        www-data    3u  IPv4  15028      0t0  TCP *:80 (LISTEN)
apache2   2413        www-data    4u  IPv4  15031      0t0  TCP *:443 (LISTEN)
apache2   2414        www-data    3u  IPv4  15028      0t0  TCP *:80 (LISTEN)
apache2   2414        www-data    4u  IPv4  15031      0t0  TCP *:443 (LISTEN)
apache2   2415        www-data    3u  IPv4  15028      0t0  TCP *:80 (LISTEN)
apache2   2415        www-data    4u  IPv4  15031      0t0  TCP *:443 (LISTEN)
apache2   2416        www-data    3u  IPv4  15028      0t0  TCP *:80 (LISTEN)
apache2   2416        www-data    4u  IPv4  15031      0t0  TCP *:443 (LISTEN)
apache2   2417        www-data    3u  IPv4  15028      0t0  TCP *:80 (LISTEN)
apache2   2417        www-data    4u  IPv4  15031      0t0  TCP *:443 (LISTEN)

doug@s15:/etc/apache2$ sudo service apache2 restart  [COLOR=#ff0000]<<< I already edited ports.conf, so now it will take effect.[/COLOR]
 * Restarting web server apache2
[Thu Nov 28 07:59:36 2013] [warn] NameVirtualHost *:90 has no VirtualHosts  [COLOR=#ff0000]<<< I didn't bother with the other required changes, so get this.[/COLOR]
[Thu Nov 28 07:59:37 2013] [warn] NameVirtualHost *:90 has no VirtualHosts

doug@s15:/etc/apache2$ [COLOR=#ff0000]sudo lsof -i -P | grep apache[/COLOR]
apache2   5623            root    3u  IPv4 278564      0t0  TCP *:80 (LISTEN)
[COLOR=#ff0000]apache2   5623            root    4u  IPv4 278567      0t0  TCP *:90 (LISTEN)[/COLOR]
apache2   5623            root    5u  IPv4 278569      0t0  TCP *:443 (LISTEN)
apache2   5628        www-data    3u  IPv4 278564      0t0  TCP *:80 (LISTEN)
[COLOR=#ff0000]apache2   5628        www-data    4u  IPv4 278567      0t0  TCP *:90 (LISTEN)[/COLOR]
apache2   5628        www-data    5u  IPv4 278569      0t0  TCP *:443 (LISTEN)
apache2   5629        www-data    3u  IPv4 278564      0t0  TCP *:80 (LISTEN)
[COLOR=#ff0000]apache2   5629        www-data    4u  IPv4 278567      0t0  TCP *:90 (LISTEN)[/COLOR]
apache2   5629        www-data    5u  IPv4 278569      0t0  TCP *:443 (LISTEN)
apache2   5630        www-data    3u  IPv4 278564      0t0  TCP *:80 (LISTEN)
[COLOR=#ff0000]apache2   5630        www-data    4u  IPv4 278567      0t0  TCP *:90 (LISTEN)[/COLOR]
apache2   5630        www-data    5u  IPv4 278569      0t0  TCP *:443 (LISTEN)
apache2   5631        www-data    3u  IPv4 278564      0t0  TCP *:80 (LISTEN)
[COLOR=#ff0000]apache2   5631        www-data    4u  IPv4 278567      0t0  TCP *:90 (LISTEN)[/COLOR]
apache2   5631        www-data    5u  IPv4 278569      0t0  TCP *:443 (LISTEN)
apache2   5632        www-data    3u  IPv4 278564      0t0  TCP *:80 (LISTEN)
[COLOR=#ff0000]apache2   5632        www-data    4u  IPv4 278567      0t0  TCP *:90 (LISTEN)[/COLOR]
apache2   5632        www-data    5u  IPv4 278569      0t0  TCP *:443 (LISTEN)
doug@s15:/etc/apache2$
doug@s15:/etc/apache2$ [COLOR=#ff0000]cat ports.conf[/COLOR]
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80
[COLOR=#ff0000]NameVirtualHost *:90
Listen 90[/COLOR]

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>
```
I don't know about your IPV6 only issue.

---

