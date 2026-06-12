---
title: "How to change localhost folder in apache2"
date: 2011-08-22
forum: Server Platforms
---

### Post by Josep CA on 2011-08-22
Hi,
I'm a noob in server managing and I have two different sites in my PC which I test locally (I use a remote hosting service when they're done). When I had only one website everything was ok but since I added the new website and I type "localhost" in my browser it drives me to the old site index.html file. I mean both sites work ok and .php pages display properly but localhost is still located in the old site. How do I can change this?
Thank you!

---

### Post by Sanados on 2011-08-22
virtual hosts: [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)


basically you write:
(ofc you can also use ip addresses instead of names)


NameVirtualHost *
<VirtualHost *>
        ServerAdmin [email]webmaster@yourdomain.com[/email]

        ServerName [www.yourdomain.com](www.yourdomain.com)
        DocumentRoot /var/www/domains/yourdomain.com/www
        <Directory /var/www/domains/yourdomain.com/www>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

<VirtualHost *>
        ServerAdmin [email]webmaster@yourdomain.com[/email]

        ServerName subdomain.yourdomain.com
        ServerAlias aliasforsubdomain.yourdomain.com

        DocumentRoot /var/www/domains/yourdomain.com/subdomain
        <Directory /var/www/domains/yourdomain.com/subdomain>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

---

### Post by Sanados on 2011-08-22
and i forgot to mention:


normal directory index are index.html
for your page to start on index.php you need to edit your apache2.conf

find the line: DirectoryIndex index.html

and change it to:
DirectoryIndex index.php index.html 
(this searches for index.php first, if not present it searches for index.html, ....)

---

### Post by Josep CA on 2011-08-23
Thank you very much for your answer. I'm sorry for the delay but finally I've able to change my httpd.conf. Now it looks like this:
```

ServerName localhost

# Make sure there's only **1** line for each of these 2 directives:
# Use for PHP 4.x:
#LoadModule php4_module	modules/libphp4.so
#AddHandler php-script	.php

# Use for PHP 5.x:

AddHandler php5-script	.php 

# Add index.php to your DirectoryIndex line:
DirectoryIndex index.html index.php

AddType text/html	.php

# PHP Syntax Coloring
# (optional but useful for reading PHP source for debugging):
AddType application/x-httpd-php-source phps

NameVirtualHost *

<VirtualHost *>
ServerName localhost
DocumentRoot /home/josep/Documents/Aceites_Escoda
<Directory /home/josep/Documents/Aceites_Escoda>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
</Directory>
</VirtualHost>

<VirtualHost *>
ServerName localhost2
DocumentRoot /home/josep/Documents/myprimarycolors
<Directory /home/josep/Documents/myprimarycolors>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
</Directory>
</VirtualHost>

```

Is this correct? How do I access now localhost1 and localhost2? I type "localhost1" and "localhost2" on firefox but I don't get my webpages.
Thank you!

---

### Post by volkswagner on 2011-08-23
I don't see a localhost1 entry, so I'd expect that would not work.

Is "localhost" working?

You need a way for the "DNS" to work.  It would be easiest to simply add to your /etc/hosts file.

Change the following:

```
127.0.0.1	localhost

```

to look like:
```

127.0.0.1	localhost localhost1 localhost2 localhost3
```


You can do "tricky" stuff with your /etc/host file.  For example, if you wanted to build a site without relative links and use the entire url such as [http://www.currentdomainproject.com](http://www.currentdomainproject.com) in your links.  You could add the domain name to your /etc/host file as above instead of localhost2.  This would force your machine to point that domain to your local machine.  Of course with this approach you would need proper apache2 virtual host entries for each domain you are working on. 

An alternative method would be to just use subdirectories.  You could add sites as a sub directory to your main site.  With this approach you would need relative links in your html, or php pages.

Assuming your sites are located at /var/www, you would add subdirectories /var/www/site1, /var/www/site2, etc.

You would then need no additional configuration (all sites would fall under the default apache config) and reach each site as follows:

[http://localhost/site1](http://localhost/site1), [http://localhost/site2](http://localhost/site2), etc.

---

### Post by Josep CA on 2011-08-23
```

127.0.0.1	localhost localhost1 localhost2 

```

Thank you for your answer volkswagner. Now when I type "localhost", "localhost1" and "localhost2" I always get to the index.html of the first page I created (that's localhost). I mean when I type "localhost1" or "localhost2" I get the same output I get when I type "localhost".

If I can't get it to work I will use the solution of using the same directory but my idea it's to use various sites since this way my html code will be more reusable.

Any ideas?
Thank you! :)

---

### Post by cgilbert16 on 2011-08-23
Have you tried using Host Headers.  You can add aliases to the sites-enabled files for apache2 so that it will know what you are looking for when you type in localhost2, 3, etc.
This can be done via the /etc/apache2/sites-enabled/ files.  Just copy the one in there and edit to add the 
 ServerName  localhost2
 ServerAlias localhost2

Make sure your path in the new one is to a different location then the first sites-enabled file and that your hosts file has the entry for resolution.

*Update* Did not see the original post date.  This must have been reengaged by the mess above

---

### Post by volkswagner on 2011-08-23
> **Josep CA said:**
> 
Thank you for your answer volkswagner. Now when I type "localhost", "localhost1" and "localhost2" I always get to the index.html of the first page I created (that's localhost). I mean when I type "localhost1" or "localhost2" I get the same output I get when I type "localhost".


Any ideas?
Thank you! :)

Make sure you have the NameVirtual host directive in ports.conf.

Add the following to /etc/apache2/ports.conf

```
NameVirtualHost *
```

Then restart apache2.

---

### Post by Josep CA on 2011-08-23
This is embarrassing...
I've found what this last problem was. NoScript was forbiding localhost1 and localhost2 scripts so Apache redirected the page to localhost.
Now everyting works perfecly. Many thanks for our time I just can't understand how I had overlooked that.

---

