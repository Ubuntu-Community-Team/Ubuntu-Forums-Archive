---
title: "No php in virtual host - only server ip"
date: 2012-08-16
forum: Server Platforms
---

### Post by mrlixam on 2012-08-16
Hey,
I am really new to ubuntu serve, so please dont mind ;)

I set up a new server (Ubuntu 11.10) with LAMP and installed webmin to make the configuration a bit more easy.
Works fine so far, expect this:

I added some virtual host (so I can handle different domains). These work fine, expecpt
that these virtual host always give an "500 Internal Sever Error".
Accessing using the server ip it works fine.

So same php file (test.php):
1XX.XXX.111/test.php (server ip) -> works fine
[http://www.domain.com/test.php](http://www.domain.com/test.php) (virtual host) -> Internal Server Error

I have no idea what this is about.
I found this post [here]("http://ubuntuforums.org/showthread.php?t=1466469"), but I am unable to 

> Update: I just got it to work.. all I needed to do was comment out the following in my virtual host config:

     Quote:
                                                 #    php_value open_basedir 1
#    php_value error_reporting "E_ALL & ~E_NOTICE"                      Is this my problem?
Where do I find this "virtual host config". 

Thanks for any help!


Here my Apache2.conf [http://pastebin.com/q3TRcQVc](http://pastebin.com/q3TRcQVc)

---

### Post by SeijiSensei on 2012-08-16
When you say you "added virtual hosts," did you create new definitions in /etc/apache2/sites-available/, then activate them by using a2ensite or by manually creating the symlinks in /etc/apache2/sites-enabled/?

When you access the server and get the 500 error, what do you see in /var/log/apache2/error.log and in /var/log/apache2/access.log?  Any hints about what's wrong.

Are you trying to use .htaccess files?  These won't work unless you permit them by editing the default virtualhost definition in /etc/apache2/sites-available/default and setting "AllowOverride" to On.  Sometimes that combination of circumstances can lead to a 500 error.

I strongly doubt the PHP error reporting settings have anything to do with your problem.

Did you read the relevant sections of the [Ubuntu Server Guide](https://help.ubuntu.com/12.04/serverguide/index.html)?

---

### Post by mrlixam on 2012-08-16
Hey, thanks for quick response.

		> When you say you "added virtual hosts," did you create new definitions  in /etc/apache2/sites-available/, then activate them by using a2ensite  or by manually creating the symlinks in /etc/apache2/sites-enabled/?

I used Webmin to do so.
But they show up in  /etc/apache2/sites-enabled/ and _a2ensite_ shows them and gives back "Site xyz already enabled" ...

> When you access the server and get the 500 error, what do you see in  /var/log/apache2/error.log and in /var/log/apache2/access.log?  Any  hints about what's wrong.
These files are empty.

> Are you trying to use .htaccess files?  These won't work unless you  permit them by editing the default virtualhost definition in  /etc/apache2/sites-available/default and setting "AllowOverride" to On.   Sometimes that combination of circumstances can lead to a 500 error.

I just try to do a php echo... nothing with .htaccess files ...
But I just changed "AllowOverride" to on.

looks like this now (the part):
```
<Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride On
        Order allow,deny
        allow from all
    </Directory>

```

But I get this error when trying to restart:

[B]```
Failed to apply changes :

Syntax error on line 11 of /etc/apache2/sites-enabled/000-default:
Illegal override option On
Action 'configtest' failed.
The Apache error log may have more information.
```

[/B]



Just checked the _/var/log/apache2/error.log_ and here this pops up all over the place:
"PHP: syntax error, unexpeced '&' in /etc/php5/apache2/php.ini on line 110

Here  /etc/php5/apache2/php.ini  from line 107 to 114
```
;   Production Value: Off

error_reporting
Default Value: E_ALL & ~E_NOTICE
Development Value: E_ALL | E_STRICT
Production Value: E_ALL & ~E_DEPRECATED

; html_errors
```


>  Did you read the relevant sections of the [Ubuntu Server Guide]("https://help.ubuntu.com/12.04/serverguide/index.html")? 	
I tried. And I Google for about 1 hour.

---

### Post by mrlixam on 2012-08-16
Hey,
okay the problem comes from here:
> 
			 				Are you trying to use .htaccess files?  These won't work unless you   permit them by editing the default virtualhost definition in   /etc/apache2/sites-available/default and setting "AllowOverride" to On.    Sometimes that combination of circumstances can lead to a 500 error. 			 		

I found a .htaccess in this directory, which I completly forgot about. Sorry.
So removing this, all works fine! Adding it again, gives error!

My    /etc/apache2/sites-available/default  looks like:

```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost

DocumentRoot /var/www
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride All
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

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

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

And I did a restart of Apache, still not working with .htaccess ... Any suggestion?

---

### Post by SeijiSensei on 2012-08-16
The easiest solution is to put whatever directives appear in .htaccess into the virtual host configuration.  .htaccess is designed to enable web site owners to change the options of their sites even if they don't have permissions to change the <VirtualHost> definition itself.

---

### Post by mrlixam on 2012-08-17
All working now!

@[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") Thanks so much!

---

