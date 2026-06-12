---
title: "Apache 2 -&gt; 403 Forbidden when accessing cgi-bin"
date: 2008-10-19
forum: Server Platforms
---

### Post by hansoffate on 2008-10-19
I have had apache2 working for quite some time now.  I have just got into learning some PERL so I would like to get cgi-bin working.  When I try to access the cgi-bin though, I get a 403 forbidden error.  I have the same permissions on the folder that I have on the index.html and mythweb.  

Any Ideas?

Thanks,
Hans

P.S.  My webserver is at [http://hans.blogsite.org](http://hans.blogsite.org)

```

hansoffate@grunt:/var/www$ ls -l
total 16
drwxr-xr-x 2 root       root       4096 2008-10-19 19:48 cgi-bin
-rwxr-xr-x 1 root       root         45 2008-04-28 01:13 index.html
lrwxrwxrwx 1 root       root         25 2008-01-06 04:40 mythweb -> /usr/share/mythtv/mythweb
```

from sites-available/default
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
                Options Indexes FollowSymLinks
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /var/www/cgi-bin/
        <Directory "/var/www/cgi-bin/">
                AllowOverride None
                Options +ExecCGI
                AddHandler cgi-script cgi pl
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

```

---

### Post by lykwydchykyn on 2008-10-20
Is your script executable?

---

### Post by hansoffate on 2008-10-20
> **lykwydchykyn said:**
> Is your script executable?

The script is executable but it doesn't matter right now.  I can't even get into the cgi-bin/ folder.  It should have the correct permissions (see first post), that's why I don't understand why it says it doesn't.

Thanks for the help.

::EDIT::
Nevermind, I thought when accessing cgi-bin, it would list out the files in the folder.  Instead, if I point it to the full path of the .pl/.cgi file, it'll actually run the script.  Thanks for the help.

---

### Post by lykwydchykyn on 2008-10-20
Ah yes.  If you want listings like that, you'd have to change: 
```

 <Directory "/var/www/cgi-bin/">
                AllowOverride None
                Options +ExecCGI
(...etc)

```
To this:
```

 <Directory "/var/www/cgi-bin/">
                AllowOverride None
                Options +ExecCGI +Indexes
(etc...)

```

---

