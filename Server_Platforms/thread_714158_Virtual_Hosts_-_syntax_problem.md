---
title: "Virtual Hosts - syntax problem?"
date: 2008-03-03
forum: Server Platforms
---

### Post by GlennB on 2008-03-03
Hi All,

I feel a bit dumb asking for help with this - I'm sure it's a simple syntax issue, but I've read a bunch, and can't fix it. I'm a newbie with Apache and it probably shows!

I'm trying to accomplish a simple task - set up virtual hosts on Apache (Gutsy LAMP server install) to use a couple of sub domains, like this:

[www.mydomain.co.uk](www.mydomain.co.uk) --> /var/www
drupal.mydomain.co.uk --> /var/www/drupal
wordpress.mydomain.co.uk --> /var/www/wordpress

I intend to have static html pages at the site root (/var/www).

This is for internal use only, so I will make the necessary additions to hosts files on workstations - there won't be any DNS involved.

I thought I could simply add virtualhost stanzas to the existing 'default' site config in /etc/apache2/sites-available and then use the existing symlink in ../sites-available. I'm doing something wrong - each of the URLs 

[www.mydomain.co.uk](www.mydomain.co.uk)
drupal.mydomain.co.uk
wordpress.mydomain.co.uk
resolves, but they all load the index.html in the main document root (/var/www). What am I doing wrong??

Here's the current 'default' file:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        ServerName thebigshed.co.uk
        ServerAlias www.thebigshed.co.uk
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride all
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
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
<VirtualHost *:80>
        ServerAdmin glenn@localhost
        DocumentRoot /var/www/drupal/
        ServerName drupal.thebigshed.co.uk
        ErrorLog /var/log/apache2/drupal-error_log common
        CustomLog /var/log/apache2/drupal-access_log common
</VirtualHost>
<VirtualHost *:80>
        ServerAdmin glenn@localhost
        DocumentRoot /var/www/wordpress/
        ServerName wp.thebigshed.co.uk
        ErrorLog /var/log/apache2/wp-error_log common
        CustomLog /var/log/apache2/wp-access_log common
</VirtualHost>

```

It's driving me nuts! Any help would be greatly appreciated.

Many thanks,

Glenn.

---

### Post by faulkes on 2008-03-03
Take the drupal and wordpress virtualhost statements out of the default file.

cd into the sites-available directory in /etc/apache2/sites-available and create 
two files "drupal" and "wordpress".  Each of those files contains the virtualhost
statements for the associated domains (i.e. at the bottom of your current 
default file).

Then run:

```

sudo a2ensite wordpress
sudo a2ensite drupal

```

This will add symlinks to /etc/apache2/sites-enabled/ for each of those sites.

restart apache.

```

sudo /etc/init.d/apache2 restart

```

And Bob should be your uncle at that point.  If not, post back and we'll go from 
whatever point you are then at.

Faulkes

---

### Post by GlennB on 2008-03-03
Thanks for the help - I'm definitely making progress now, thanks to this input.

I pulled the virtualhost sections into their own files, so I now have two new virtual hosts files in sites-available, with the appropriate symlinks in sites-enabled.

I sorted out a few errors like this:

```
[error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
``` by making things consistent, and  ```
apache2ctl configtest
``` 

now thinks the syntax is ok. The two new virtual hosts files look like this:

wordpress:

```
<VirtualHost *:80>
        ServerAdmin glenn@localhost
        DocumentRoot /var/www/wordpress/
        ServerName wp.thebigshed.co.uk
        ErrorLog /var/log/apache2/wp-error_log
        CustomLog /var/log/apache2/wp-access_log common
</VirtualHost>
```

This works just fine - I can enter [http://wp.thebigshed.co.uk](http://wp.thebigshed.co.uk) into my browser and it takes me to exactly the right place.

The second file isn't such happy news...

drupal:

```
<VirtualHost *:80>
        ServerAdmin glenn@localhost
        DocumentRoot /var/www/drupal/
        ServerName drupal.thebigshed.co.uk
        ErrorLog /var/log/apache2/drupal-error_log
        CustomLog /var/log/apache2/drupal-access_log common
</VirtualHost>
```

This gives me a 500 internal server error! I checked the error log and found this:

```
[alert] [client 192.168.1.14] /var/www/drupal/.htaccess: Option Indexes not allowed here
``` 

so I guess the bug hunting goes on - I now have to suss out why the .htaccess is messing things up - something else to learn!

Many thanks,

Glenn.

---

### Post by bmathis on 2008-03-04
This may be a stupid question, but does www-data have permissions for the drupal folder?

---

### Post by GlennB on 2008-03-04
> **bmathis said:**
> This may be a stupid question, but does www-data have permissions for the drupal folder?

Yes, it does. In fact, the Drupal content works fine if I reach it by using a URL in this form:

```
http://ip.to.server/drupal
```

I did some Googling, and it looks as if Drupal doesn't behave the same way with the default .htaccess file when it's running in a virtual host. I haven't yet worked out exactly why, or how to fix it though.

Thanks for the input,

Regards,
Glenn.

---

### Post by Alekc on 2008-03-04
You should take a look on "AllowOverride" directive of apache. Infact this error derive from fact that drupal is trying to change some options with .htaccess but i suppose that AllowOverride is setted to none. 

Try to see this post (first result from google) [http://drupal.org/node/18852](http://drupal.org/node/18852)

P.s. check if mod_rewrite is enabled 
"sudo a2enmod rewrite"

---

### Post by GlennB on 2008-03-04
> **Alekc said:**
> You should take a look on "AllowOverride" directive of apache. 

That was it... I changed the virtual host file for the 'drupal' subdomain to include this section:

```
<Directory /var/www/drupal/>
                Options Indexes FollowSymLinks +Includes
                AllowOverride All
                Order allow,deny
                allow from all
</Directory>
```

It now works fine! [www.blah](www.blah), drupal.blah and wp.blah now all resolve exactly as I want.

Thanks for the help everyone.

Regards,

Glenn.

---

### Post by Railsbuntu on 2008-03-05
> 'm trying to accomplish a simple task - set up virtual hosts on Apache (Gutsy LAMP server install) to use a couple of sub domains, like this:

[www.mydomain.co.uk](www.mydomain.co.uk) --> /var/www
drupal.mydomain.co.uk --> /var/www/drupal
wordpress.mydomain.co.uk --> /var/www/wordpress

I intend to have static html pages at the site root (/var/www).

This is for internal use only, so I will make the necessary additions to hosts files on workstations - there won't be any DNS involved.
Hi,

I am having the same problem.

I'd like to setup locally on my network a server that can be reached by typing [www.myserver.com](www.myserver.com)

I'd like to also have subdomains such as: phpmyadmin.myserver.com

Can you show me your etc/hosts file please? Or any other file that can emulate this behaviour.

Each time I type [www.myserver.com](www.myserver.com) on a local client machine, it goes all the time on internet.

---

### Post by GlennB on 2008-03-10
Hi,

I'm at work at the moment, so I don't have access to the hosts file from one of the client machines, but basically each machine on the network that needs to access the server using domains like this:

wp.mydomain.com
[www.mydomain.com](www.mydomain.com)
drupal.mydomain.com

Needs to have multiple entries in the hosts file with the same ip address referenced. For example :

192.168.21.239  [www.mydomain.com](www.mydomain.com)
192.168.21.239  wp.mydomain.com
192.168.21.239  drupal.mydomain.com

This way, traffic for any of those subdomains will be routed to the same server, and Apache can figure out which page  to offer up depending on the URL that called it.

Hope that helps,

Glenn.

---

### Post by Railsbuntu on 2008-03-12
Hi GlennB,

Thanks for your reply. I have been able to handle the subdomains in the webserver by configuring the correct virtualhosts, I had my definitions wrong, so it couldn't work.

Cheers,
:popcorn:

---

### Post by benne on 2008-03-13
first of all, i would recomend a different directory structure.

/var/www/thebigshed.co.uk
/var/www/drupal.thebidshed.co.uk
/var/www/wordpress.thebigshed.co.uk

Check your vhost config files. It seems to me like you are using "NameVirutalHost *" (without port number) and <VirutalHost *:80> (with port number)

Make sure all are with port numbers or without. Preferrable with, then you can add https later on if you want to. 

Otherwise, you config looks fine.

---

