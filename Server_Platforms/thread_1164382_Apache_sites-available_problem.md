---
title: "Apache sites-available problem"
date: 2009-05-19
forum: Server Platforms
---

### Post by kahuna0789 on 2009-05-19
To give a little background, I have been hosting my website under the /var/www folder for... about a year. I recently started hosting a few other peoples websites which i placed under ~/public_html (being their home). That went off pretty much without a problem.

Now I decided to move my original website to my home directory much like I had theirs.... this is where I ran into my problem. Upon reloading apache2 I get.

```
 
* Reloading web server config apache2
[Tue May 19 15:38:16 2009] [warn] NameVirtualHost *:0 has no VirtualHosts

```Which is odd considering my default config file looks like...

```

NameVirtualHost *
<VirtualHost *>
    ServerName site1.mysite.org     
    ServerAdmin kahuna@mysite.org 
    
    DocumentRoot /home/site1/public_html
    
    <Directory /home/site1/public_html>
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
<VirtualHost *>
    ServerName site2.othersite.com
    DocumentRoot /home/site2/public_html

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/site2.log combined
</VirtualHost>

<VirtualHost *>
        ServerName site3.anothersite.net
        DocumentRoot /home/site3/public_html 
    # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/codegods.log combined
    #squirrelmail config
    Alias /squirrelmail/ "/usr/share/squirrelmail"

    <Directory "/usr/share/squirrelmail">
          Options Indexes FollowSymLinks
          <IfModule mod_php4.c>
                php_flag register_globals off
          </IfModule>
          <IfModule mod_php5.c>
                php_flag register_globals off
          </IfModule>
          <IfModule mod_dir.c>
                DirectoryIndex index.php
          </IfModule>

          # access to configtest is limited by default to prevent information leak
          <Files configtest.php>
                order deny,allow
                deny from all
                allow from 127.0.0.1
          </Files>
    </Directory>
</VirtualHost>

```Since I have virtual hosts... im kind of at a loss to find the problem here. Any ideas? If you need any other information let me know.

Thanks :)
Kahuna0789

---

### Post by cdenley on 2009-05-19
Post this output:
```

grep NameVirtualHost /etc/apache2/*.conf /etc/apache2/sites-enabled/* /etc/apache2/conf.d/*

```

---

### Post by kahuna0789 on 2009-05-19
Output:
```

root@server:/etc/apache2/sites-available# grep NameVirtualHost /etc/apache2/*.conf /etc/apache2/sites-enabled/* /etc/apache2/conf.d/*
/etc/apache2/sites-enabled/000-default:NameVirtualHost *

```

---

### Post by mbeach on 2009-05-19
what file are you using for your 'default config file'?  Is it /etc/apache2/apache2.conf?

It may be helpul to understand the virtual host setup in Debian/Ubuntu and how it allows for easy disabling/enabling of particular sites. 

I've seen your warning only when you are calling that directive more than once (others have too: [http://ubuntuforums.org/archive/index.php/t-312916.html](http://ubuntuforums.org/archive/index.php/t-312916.html)).  Also, take a read of /usr/share/doc/apache2/README.Debian.gz as I think your issue is covered there as well.

I suspect cdenley was trying to find where you had it set it mulitple places.

try:
```
grep -iR NameVirtualHost /etc/apache2/*.conf
```

---

### Post by kahuna0789 on 2009-05-19
Command output:
```

root@server:/etc/apache2/sites-available# grep -iR NameVirtualHost /etc/apache2/*.conf
root@server:/etc/apache2/sites-available#

```no results in the conf file, the only place im working with the virtual hosts is in the 
/etc/apache2/available-sites/000-default (aka /etc/apache2/enabled-sites/default)
which is the site that is enabled by default when you install apache2... which has been working fine before changing the first virtual hosts directory... 

maybe theres something in the conf file i need to change to coincide with the change from /var/www to ~/public_html?

Thanks
Kahuna0789

---

### Post by mbeach on 2009-05-19
do you have anything in /etc/apache2/ports.conf?

by the way, I believe the idea is to have a file in /sites-available for each site your are running. Not completely necessary as you have seen, but allows you to use the a2ensite and a2dissite commands to enable and disable a site. When you use the a2ensite, it will create a symbolic link in /sites-enabled. When loaded by apache, the enabled sites are loaded in alphabetical order. 

Have you read over:
/usr/share/doc/apache2/NEWS.Debian.gz

---

### Post by kahuna0789 on 2009-05-19
yeah i know you can keep separate files for each, but combining them has been working for the most part... at least until now

to answer your question i haven't modified any other config files for this other than the hosts file... but that was before the problem.

---

### Post by cdenley on 2009-05-20
The output he posted shows that there aren't multiple NameVirtualHost lines in any file I can think of, unless it's with the modules. Also, apache doesn't accept "0" as a valid port, so I'm not sure what would result in that warning. Did you try restaring apache, not just reloading? Does it still work, since the message is a "warning" and not an "error"?

---

### Post by mbeach on 2009-05-20
which version of apache are you using? I'm wondering if there is any chance you've upgraded Apache and the installer has amended your files.
```
apache2 -v
```

and if you'd mind trying with a variation of the above to put that possibility to bed:
```
grep -iR NameVirtualHost /etc/apache2/*
```

---

### Post by kahuna0789 on 2009-05-20
```

root@server:~# grep -iR NameVirtualHost /etc/apache2/*
/etc/apache2/sites-available/default:NameVirtualHost *
/etc/apache2/sites-enabled/docs/default:NameVirtualHost *
/etc/apache2/sites-enabled/000-default:NameVirtualHost *

``````

root@server:/etc/apache2/sites-enabled# ls -l
total 0
lrwxrwxrwx 1 root root 36 2009-01-03 01:04 000-default -> /etc/apache2/sites-ava   ilable/default
lrwxrwxrwx 1 root root 28 2009-05-18 17:52 docs -> /etc/apache2/sites-available

```Silly me, forgot to remove the symlink when I deleted the file in sites-available... and then apparently it defaulted to pointing to the directory.

Thanks all
Kahuna0789

---

