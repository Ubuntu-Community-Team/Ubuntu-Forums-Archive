---
title: "Enter http://&lt;ip&gt; goes to webmail.domain.com"
date: 2015-02-08
forum: Server Platforms
---

### Post by phs2004 on 2015-02-08
Hi

Software
apache2
roundcube webmail

When enter my ip like [http://85.30.159.249](http://85.30.159.249) I come to webmail.mydomain.com instead of my [www.linuxburken.com](www.linuxburken.com) Have tryed alot of ways to change it but need help cant sort it out. 

Virutalhosts confs: 

```
<VirtualHost *:80>        
        ServerAdmin webmaster@localhost
        ServerName www.linuxburken.com
        ServerAlias linuxburken.com
        ServerAlias *.linuxburken.com
        DocumentRoot /var/www/html


        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        #


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf


 AssignUserId anders anders


</VirtualHost>



```

```

<VirtualHost *:80>
ServerName webmail.linuxburken.com
DocumentRoot /usr/share/roundcube/
</VirtualHost>




# Access to tinymce files
<Directory "/usr/share/tinymce/www/">
      Options Indexes MultiViews FollowSymLinks
      AllowOverride None
      <IfVersion >= 2.3>
        Require all granted
      </IfVersion>
      <IfVersion < 2.3>
        Order allow,deny
        Allow from all
      </IfVersion>
</Directory>


<Directory /var/lib/roundcube/>
  Options +FollowSymLinks
  # This is needed to parse /var/lib/roundcube/.htaccess. See its
  # content before setting AllowOverride to None.
  AllowOverride All
  <IfVersion >= 2.3>
    Require all granted
  </IfVersion>
  <IfVersion < 2.3>
    Order allow,deny
    Allow from all
  </IfVersion>
</Directory>


# Protecting basic directories:
<Directory /var/lib/roundcube/config>
        Options -FollowSymLinks
        AllowOverride None
</Directory>


<Directory /var/lib/roundcube/temp>
        Options -FollowSymLinks
        AllowOverride None
        <IfVersion >= 2.3>
          Require all denied
        </IfVersion>
        <IfVersion < 2.3>
          Order allow,deny
          Deny from all
        </IfVersion>
</Directory>


<Directory /var/lib/roundcube/logs>
        Options -FollowSymLinks
        AllowOverride None
        <IfVersion >= 2.3>
          Require all denied
        </IfVersion>
        <IfVersion < 2.3>
          Order allow,deny
          Deny from all
        </IfVersion>
</Directory>




```

Anything out of the order here or? Tyed all differnt things but still when enter ip i get to webmail.

---

### Post by volkswagner on 2015-02-08
When you don't specify a domain name apache will server the first alpha-numeric conf file.

I'm guessing the vhost conf file for webmail comes before the desired site (alpha-numerically)

What's the output of:
```
ls -al /etc/apache2/sites-enabled
```

---

### Post by phs2004 on 2015-02-08
Roundcube dont show up its in /etc/apache/conf-enabled. Maby thats the problem, think im going to test and see if i can rm that conf and add it to vhost.

---

### Post by Habitual on 2015-02-08
Why ya using [ServerAlias]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") but not a named virtual host?

---

### Post by phs2004 on 2015-02-08
If I remove serveralias and type [www.linuxburken.com]("http://www.linuxburken.com") then roundcube show up??? sone I remove roundcube and use squirrelmail. It has been working for years and years. THis new roundcube makes all things crasy.

roundcube uses an apache.conf in /etc/roundcube/ and ln -s to /etc/apache2/conf-avalible. You can see the conf in top

I think i auto installed roundcube whit apt-get install roundcube. Going to test remove it and install it manually.

---

### Post by volkswagner on 2015-02-08
> **Habitual said:**
> Why ya using [ServerAlias]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html") but not a named virtual host?

What makes you think he's not using NamedVirtualHosts?

FYI, ServerAlias can be a space separated list, so there's no need for multiple lines.

Uninstalling seems a bit extreme.

You never posted output of:
```
ls -al /etc/apache2/sites-enabled
```

If you have 000-default enabled you should use that to direct apache to the directory what you'd like
to server when no hostnames match.

---

### Post by phs2004 on 2015-02-08
```

root@linuxburken:/etc/apache2/sites-enabled# ls -al /etc/apache2/sites-enabled
totalt 8
drwxr-xr-x 2 root root 4096 feb  8 20:26 .
drwxr-xr-x 9 root root 4096 jan 28 08:23 ..
lrwxrwxrwx 1 root root   35 apr 17  2014 000-default.conf -> ../sites-available/000-default.conf
lrwxrwxrwx 1 root root   30 apr 17  2014 henrik.conf -> ../sites-available/henrik.conf
lrwxrwxrwx 1 root root   37 apr 17  2014 roninofsweden.conf -> ../sites-available/roninofsweden.conf
lrwxrwxrwx 1 root root   29 aug 25 09:10 stats.conf -> ../sites-available/stats.conf
root@linuxburken:/etc/apache2/sites-enabled#




```

---

### Post by CharlesA on 2015-02-08
Remove 000-default.conf and restart apache.

See what happens.

---

### Post by phs2004 on 2015-02-08
Thats to my [www.linuxburken.com](www.linuxburken.com) then that wont work :) Maby make new for linuxburken.com and then remove it?

---

### Post by phs2004 on 2015-02-08
```

a2dissite [COLOR=#000000] 000-default.conf

[/COLOR]service apache2 reload 

```

everying *.linuxburken.com goes to roundcube :)

---

### Post by phs2004 on 2015-02-08
I tryed comment out Vhost in apache conf for roundcube and made a new vhost whit that info. Dident work.  

apache.conf in /etc/roundcube/apache.conf
```

#<VirtualHost *:80>
#ServerName webmail.linuxburken.com
#ServerAlias mail.* webmail.*
#DocumentRoot /usr/share/roundcube/
#</VirtualHost>



```

---

### Post by volkswagner on 2015-02-08
What's in /etc/apache2/conf.d

---

### Post by phs2004 on 2015-02-08
only owncloud.conf. in ubuntu 14.04 server all conf are in /etc/apache2/conf-available 

```

root@linuxburken:/etc/apache2/conf-available# lscharset.conf            localized-error-pages.conf    owncloud.conf    roundcube.conf  serve-cgi-bin.conf
javascript-common.conf  other-vhosts-access-log.conf  phpmyadmin.conf  security.conf

```

---

### Post by phs2004 on 2015-02-08
I have installed roundcube 1.05 going to remove that old 0.94. And make a vhost subdomain for the new one.

edit: works fine now whit its own vhost :)

---

