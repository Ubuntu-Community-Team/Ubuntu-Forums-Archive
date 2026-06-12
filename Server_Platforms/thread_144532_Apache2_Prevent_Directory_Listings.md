---
title: "Apache2: Prevent Directory Listings"
date: 2006-03-14
forum: Server Platforms
---

### Post by nick1 on 2006-03-14
I first started using Apache on Fedora Core 4 and was used to having all the config settings in httpd.conf. Now that I'm using Ubuntu 5.10 (Breezy Badger), I've noticed the Apache settings are handled a bit differently. There's an apache2.conf file, httpd.conf file, and ports.conf file.

In order to prevent listing the contents of /var/www/testdir (using the indexes method), I had to edit the httpd.conf file, as shown below:

```
# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
#
[b]<Directory "/var/www/testdir">
  Options -Indexes
</Directory>[/b]
```

That's the entire content of my httpd.conf. Isn't there supposed to be a lot more in this file?

Another option to prevent listing the contents of /var/www/testdir (using the indexes method), was to edit /etc/apache2/sites-available/default. Here are the contents of that file:

```
NameVirtualHost *
<VirtualHost *>
    ServerAdmin webmaster@localhost
    
    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options **Indexes**FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
        # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined
    ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

I removed **Indexes **from:

```
<Directory /var/www/>
    Options **Indexes**FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
```

Even though it now does what I want it to, I'm very confused and wondering if I'm editing settings in the right place. Can someone please explain why things are quite different in Ubuntu compared to FC4? Why not just one file to edit, httpd.conf? I guess I'm just trying to understand Ubuntu's way of doing things.  A nice visual layout of what-goes-where in Apache2 would be awesome.  

Thanks a lot,

*Nick*

---

### Post by Koybe on 2006-03-14
This way is the same as debian way.

It's just a question of organisation. Nothing else to deal with. I personnaly feel it like a way to make the server mor modulable. So it's easier to add/remove site/modules.
So you got :

*Fedora : *
[LIST=1]
[*]/etc/httpd/conf/httpd.conf (one big file)
[*]/etc/httpd/conf.d/
[/LIST]

*Debian :*
[LIST=2]
[*]/etc/apache2/apache2.conf+httpd.conf+ports.conf
[*]/etc/apache2/conf.d/
[/LIST]
The conf.d directory works exactly the same way.

Then debian adds :
[list]/etc/apache2/mods-available[/list]
[list]/etc/apache2/mods-enable[/list]
[list]/etc/apache2/sites-available[/list]
[list]/etc/apache2/sites-enable[/list]

You got 4 commands to manipulate this :
```
a2enmod
a2dismod
a2ensites
a2dissites

```Those comands are just making symlinks from the available directory to the enabled directory which is included in your apache2.conf

So in your case the best way is to set Indexes in your default web site. Or to remove the default web site if you only want websites of your own and add it in the definition of the site.

I hope it's a bit more clear :)

---

