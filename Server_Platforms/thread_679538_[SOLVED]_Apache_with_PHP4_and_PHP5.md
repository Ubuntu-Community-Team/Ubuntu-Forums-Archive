---
title: "[SOLVED] Apache with PHP4 and PHP5"
date: 2008-01-27
forum: Server Platforms
---

### Post by Temujin_12 on 2008-01-27
I'm trying to setup php4 and php5 for a single installation of apache.  I installed using the instructions from [here]("http://www.howtoforge.com/apache2_with_php5_and_php4_p2").  Basically, PHP5 is loaded as a module and PHP4 is done through CGI.  The instructions are for 5.10 and I am running 6.10.  I can't imagine there being significant differences, but I could be wrong.

PHP5 works great (ie: <?php phpinfo(); ?> shows up just fine.  However, when I try to configure a vhost to use PHP4 (from cgi), it either doesn't parse (ie: it just echo's out the PHP source) or it dumps the following error:
```
[an error occurred while processing this directive] The requested URL was not found on this server. If you entered the URL manually please check your spelling and try again. 
```

What URL is it talking about from above?

I've also tried following the instructions [here]("http://wiki.apache.org/httpd/PHP4AndPHP5"), but to no avail (this just ends up showing the source of the file).

Here's my vhost config:
```
<VirtualHost XXX.XXX.XXX.XXX:443>
        ServerAdmin admin@localhost
        DocumentRoot /home/site/www/htdocs
        ServerName site.com
        ServerAlias site.com
        ErrorLog /var/log/apache2/site.com/error.log
        CustomLog /var/log/apache2/site.com/access.log combined
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        # remove PHP5 and use PHP4
        #RemoveHandler .php .html
        #RemoveType .php .html
        #AddType php-script .php .html
        AddHandler php-script .php .html
        Action php-script /cgi-bin/php4
        #AddType application/x-httpd-php .php .html

        php_value include_path ".:/home/site/www/site.com/scripts:/home/site/www/site.com/scripts/pear"
        php_value output_buffering "4096"
</VirtualHost>
```

I've tried just about every combination of RemoveHandler, RemoveType, AddType, AddHandler, Action, and AddType... but to no avail.


I ran across a post describing how they had to define the /cgi-bin/php4 directory by adding the following to the vhost:
```
<IfModule mod_cgi.c>
     <Location /cgi-bin/php4>
          SetHandler cgi-script
          Options ExecCGI
    </Location>
</IfModule>
```

...but this didn't seem to do anything.

Does someone have an example config that works with apache defaulting to PHP5 and specific vhosts using PHP4?

---

### Post by Temujin_12 on 2008-01-27
I'm going to shamelessly bump this back up to the top to see if anyone out there  has any ideas or suggestions.

Has anyone out there gotten PHP4 (via CGI) and PHP5 via a module to work with apache2?  If so, could you share your apache configs?

---

### Post by Temujin_12 on 2008-01-28
I figured it out.

Looking in my apache error log I noticed this:
```
script '/home/site/htdocs/cgi-bin' not found or unable to stat
```

...whenever my vhost was configured with the following:
```

AddHandler php-script .php .html
Action php-script /cgi-bin/php4
```

Poking around the apache documentation I found the [ScriptAlias directive]("http://httpd.apache.org/docs/2.0/mod/mod_alias.html#scriptalias").

I added the following to my vhost:
```
ScriptAlias /cgi-bin/php4 /usr/lib/cgi-bin/php4
```

...and now PHP 4 works for this vhost!  Now I can specify whether I want a particular vhost to PHP5 or PHP4.

Hope this helps someone else trying to figure this out.

---

### Post by googlah on 2008-01-28
Thanks for sharing. :)

---

### Post by Temujin_12 on 2008-01-29
I ended up doing one more piece of configuration.  I also needed each vhost to be able to configure its own include_path (as well as other php_value's).

Looking at [PHP's How to change configuration settings manual]("http://us3.php.net/configuration.changes"), I noticed that PHP under CGI will NOT respond to php_value statements in Apache's configuration files.  Fortunately, a user [submitted instructions on how to do this]("http://us3.php.net/configuration.changes#76362").  They explain it very well, so if you need to not only specify whether a vhost uses PHP4 or PHP5 but also need to further configure PHP settings per vhost, follow those instructions.

So, I have the following now to set this up:

vhost snippet:
```

# use PHP4
ScriptAlias /cgi-bin/php4 /home/site/php4-custom.cgi
AddHandler php-script .php .html
Action php-script /cgi-bin/php4
```

/home/site/php4-custom.cgi:
```
#!/bin/sh
export PHPRC=/home/site
exec /usr/lib/cgi-bin/php4
```

And copied PHP4's main php.ini file (mine was in /etc/php4/cgi/php.ini) to /home/site/, and made whatever changes I needed in there.

So, when a vhost is configured using the snippet above it will run .php and .html files through '/home/site/php4-custom.cgi' which in turn just runs '/usr/lib/cgi-bin/php4' but tells it to use a specific php.ini (that's what the 'export PHPRC=/home/site' line does).

This turned out to be very helpful as I needed to change more than just the include_path to get this particular site to work.  The nice thing about this setup is you now have the ability to not only specify PHP5 or PHP4 per vhost but further configure whatever you want about PHP for that vhost.  This seems to me (assuming it doesn't introduce any security vulnerabilities beyond what PHP or CGI do themselves) to be a very flexible setup which would allow a single apache installation to have a wide range of PHP sites with varying PHP requirements.  In theory, you could do this same thing to even provide support for PHP3 (which I don't suggest doing).

Again, hope this saves someone some time in setting this up.

---

