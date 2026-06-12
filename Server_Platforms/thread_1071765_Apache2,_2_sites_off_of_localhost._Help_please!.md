---
title: "Apache2, 2 sites off of localhost. Help please!"
date: 2009-02-16
forum: Server Platforms
---

### Post by z0mbi3 on 2009-02-16
Just a quick one I'm relatively confident someone here can help me with.

Basically I have apache2 running on Ubuntu Server 8.10 in a VM. I had my 000-default in sites-available (and sites-enabled) configured to point [http://localhost/smarrt](http://localhost/smarrt) to /var/www/smarrt. This worked fine and I could access the site off that path no problem.

Later on I tried installing ezweb ([http://ezweb.morfeo-project.org/](http://ezweb.morfeo-project.org/)) as I want to be able to do some development on it. Ezweb is just a web based tool that installs off of their own Ubuntu repository. Anyway it installed fine, and I can now access ezweb by going to [http://localhost](http://localhost). Only trouble is that now [http://localhost/smarrt](http://localhost/smarrt) no longer takes me to the site that I mentioned before.

I checked and I still have my 000-default file there as before, but now I also have 010-ezweb-platform. I tried running a2disite against 010-ezweb-platform but it told me that that site wasn't enabled, and when I ran a2ensite agaisnt 000-default it told me it was already enabled.

Apache2 configurations aren't something I know amazingly well, so if someone could give me some pointers I'd really appreciate it. What I really want to be able to do is set it up so that [http://localost/ezweb](http://localost/ezweb) takes me to easyweb, and [http://localhost/smarrt](http://localhost/smarrt) takes me to the other site I mentioned earlier.

Thanks in advance.

---

### Post by inphektion on 2009-02-16
someone who is familiar with ezweb would surely know what it did.  but as a guess what files are in /etc/apache2/conf.d?
you see any ezweb config stuff there?

---

### Post by unixeducation on 2009-02-17
You may want to install something like ISPConfig on your server to faciliate easy site management; I use it on both internal and production servers. Link: [http://www.ispconfig.org](http://www.ispconfig.org)

---

### Post by z0mbi3 on 2009-02-17
Well a little update. I tried copying 000-default over 010-ezweb-platform and now [http://localhost/smarrt](http://localhost/smarrt) works as before, and expectedly [http://localhost](http://localhost) no longer points to ezweb.

However this is confusing me as a2ensite and a2disite tell me (or told me) that 010-ezweb-platform was disabled.

Any one got any ideas? I couldn't really see anything relevant in conf.d.

edit:

Worth noting I could use something like ispconfig, in fact I might in the future, however I'd like to understand the config behind apache2 and how I deal with a problem like the one I'm having from the command line.

---

### Post by Phlee on 2009-02-17
Make sure your 010-ezweb-platform is in the /etc/apache2/sites-available.  Then when you run a2ensite it will create sym links to /etc/apache2/sites-enabled and enable the conf.

---

### Post by z0mbi3 on 2009-02-17
> **Phlee said:**
> Make sure your 010-ezweb-platform is in the /etc/apache2/sites-available.  Then when you run a2ensite it will create sym links to /etc/apache2/sites-enabled and enable the conf.

I think you're missing the point here. 010-ezweb-platform is working fine, the problem is that it seems to be superseding 000-default.

---

### Post by inphektion on 2009-02-17
post ls -la list of sites-enabled dir and post the contents of the 000-default and ezweb files that have the site config in them.

---

### Post by z0mbi3 on 2009-02-17
> **inphektion said:**
> post ls -la list of sites-enabled dir and post the contents of the 000-default and ezweb files that have the site config in them.

As requested:

```
z0mbi3@z0mbi3:/etc/apache2/sites-enabled$ ls
000-default  010-ezweb-platform

```

000-default:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
    Alias /smarrt/ "/var/www/smarrt/"
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

010-ezweb-platform:

```
NameVirtualHost *

<VirtualHost *>
  ServerAdmin webmaster@localhost

  ServerName localhost

  DocumentRoot /var/www/ezweb-platform/

  ErrorLog /var/log/apache2/ezweb-error.log

  LogLevel warn

  CustomLog /var/log/apache2/ezweb-access.log combined

  ServerSignature On

  <Location />
    SetHandler python-program
    PythonHandler django.core.handlers.modpython
    SetEnv DJANGO_SETTINGS_MODULE settings

    PythonPath "['/usr/share/ezweb-platform'] + sys.path"
  </Location>

  Alias /media /usr/share/python-support/python-django/django/contrib/admin/media
  Alias /site-media /usr/share/ezweb-platform/media
  Alias /repository /var/www/gadgets

  <Location /media>
    SetHandler None
  </Location>

  <Location /site-media>
    SetHandler None
  </Location>

  <Location /repository>
    SetHandler None
  </Location>

  <Directory /var/www/gadgets>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
  </Directory>

</VirtualHost>

```

---

### Post by z0mbi3 on 2009-02-20
Sorry to bump this one guys but I'm still in a fix with this. 

Anyone got any ideas? I'm sure it's just something fundamental I'm not understanding.

---

