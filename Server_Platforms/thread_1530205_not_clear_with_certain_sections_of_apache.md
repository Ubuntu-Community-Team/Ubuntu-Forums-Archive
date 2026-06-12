---
title: "not clear with certain sections of apache"
date: 2010-07-13
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-13
I am not clear with certain sections of apache I saw a default virtual host file.
as follows
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

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128

```

In the above file I am not clear with

```

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

```
What does Directory / here represents is it same as document root or different.

The following section where /var/www is included in Directory Index
```

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```
What does Options Indexes FollowSymLinks MultiViews
in above structure do and why is   Directory /var/www/
section existing by default.

In the following section 
ScriptAlias
```

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>


```
I am not clear as why by default ScriptAlias is present in the default vhost is it necessary to keep in other Virtual Hosts.



Similarly /doc/ what is this referring to 
in following section
```

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128

```
I checked this page
[http://httpd.apache.org/docs/2.0/mod/core.html#directory](http://httpd.apache.org/docs/2.0/mod/core.html#directory)
I feel this topic needs much more coverage than the documentation is (from point of view of security also)
if some one can share some link/best practises or their experience that would be great and help newcomers.

---

### Post by zabuch on 2010-07-13
> **tapas_mishra said:**
> 
```

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

```What does Directory / here represents is it same as document root or different.

This is not a document root - but the root of your filesystem. It's like setting default options for every file that may be server by Apache on your filesystem. That's because <Directory / > will apply to your root directory (/) and all the directories below. You can think about this one as setting default options.

> **tapas_mishra said:**
> 
```

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```What does Options Indexes FollowSymLinks MultiViews
in above structure do and why is   Directory /var/www/
section existing by default.


This time we override the default configuration (/) just for files served from /var/www. This section exists because you usually (by convention) put files to be served by Apache inside /var/www. The Options will allow some for some actions to be performed - see [http://httpd.apache.org/docs/2.0/mod/core.html#options](http://httpd.apache.org/docs/2.0/mod/core.html#options) . You usually want these actions to be limited by default (in Directory /) but some of them enabled for /var/www (Directory /var/www)

---

### Post by tapas_mishra on 2010-07-13
```

<Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory> 
```
Then what is the importance of <Directory / > statement ?
Is there any security problem if this is missed ?

---

