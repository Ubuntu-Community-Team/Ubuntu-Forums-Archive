---
title: "Apache2 Virtual Hosts Problem"
date: 2008-04-26
forum: Server Platforms
---

### Post by vital101 on 2008-04-26
Hey everyone,

I've recently been dabbling in Virtual Hosts using Apache2.  I have two domains pointing to the same server, I have my virtual hosts set up to direct traffic to two different spots.  Here's my httpd.conf file.

```

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

NameVirtualHost 192.168.1.101:80

<VirtualHost 192.168.1.101:80>
ServerName thedevforum.com
ServerAlias www.thedevforum.com
DocumentRoot /var/www/phpBB3
</VirtualHost>

<VirtualHost 192.168.1.101:80>
ServerName re-cycledair.com
ServerAlias www.re-cycledair.com
DocumentRoot /var/www/wordpress
</VirtualHost>

```

The problem is that whether you go to re-cycledair.com or thedevforum.com, that both always go to /var/www/phpBB3.  Even if I go directly to the ip address, I still get directed there.  I've tried retstarting apache more than once, and I even rebooted the system.

This is on Dapper, running Apache2.

Thanks,
vital101

---

### Post by Oldsoldier2003 on 2008-04-27
> **vital101 said:**
> Hey everyone,

I've recently been dabbling in Virtual Hosts using Apache2.  I have two domains pointing to the same server, I have my virtual hosts set up to direct traffic to two different spots.  Here's my httpd.conf file.

```

# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so

NameVirtualHost 192.168.1.101:80

<VirtualHost 192.168.1.101:80>
ServerName thedevforum.com
ServerAlias www.thedevforum.com
DocumentRoot /var/www/phpBB3
</VirtualHost>

<VirtualHost 192.168.1.101:80>
ServerName re-cycledair.com
ServerAlias www.re-cycledair.com
DocumentRoot /var/www/wordpress
</VirtualHost>

```

The problem is that whether you go to re-cycledair.com or thedevforum.com, that both always go to /var/www/phpBB3.  Even if I go directly to the ip address, I still get directed there.  I've tried retstarting apache more than once, and I even rebooted the system.

This is on Dapper, running Apache2.

Thanks,
vital101

don't edit httpd.conf- instead each site needs a conf in 
/etc/apache2/sites-available

then use a2ensite <conffilename> to enable the second site. 

you might also need to set up rewrite rules to forward your inbound requests to the appropriate site since they are listening to the same port on the same ip.(unless you are doing some dns magic somewhere else )

---

