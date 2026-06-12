---
title: "Basic Apache Problem - trying to host a website"
date: 2010-05-06
forum: Server Platforms
---

### Post by Demented ZA on 2010-05-06
Hi everyone!

I'm trying to host a website on my Ubuntu 10.04 server. My server is available directly on the internet. I can ssh into it etc. I have a dynamic IP address and a dyndns domain name: myname.dyndns.biz

Upon installing ubuntu, I selected web server software to be installed wich installed LAMP. (Linux, Apache etc).

What I want to do:

I want to host a web page, in order to understand how it works, and then later replace it with a webmail sollution. 

Now the part I'm getting stuck with:

How do I create an alias/virtual host to display my webpage on the internet using [http://myname.dyndns.biz/website](http://myname.dyndns.biz/website)  ?

What I know so far:

What I read up on the internet over the past two/three days is the following: 
(bear with me, this differs from version to distro to person:confused:)

I have a website under /home/user/website/index.php

1) I copy /etc/apache2/sites-available/default to /etc/apache2/sites-available/website
```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/website
```2)I then edit /etc/apache2/sites-available/website using:
```
sudo nano /etc/apache2/sites-available/website
```3) I make /etc/apache2/sites-available/website look like this:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /home/user/website
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /home/user/website>
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
        Allow from all

    </Directory>

</VirtualHost>
```4)use a2ensite to enable the site:

```
sudo a2ensite website
```5)Restart apache:
```
sudo /etc/init.d/apache2 restart
```[CENTER]****or****
[/CENTER]
```
sudo /etc/init.d/apache2 force-reload
```now I should be able to navigate to [http://myname.dyndns.biz/website](http://myname.dyndns.biz/website) to load the page?

In practice, this is not working:
When I navigate to the url above, I get a "The requested URL /website was not found on this server."


What am I doing wrong??

Thanks in advance

---

### Post by Black_Prince on 2010-05-06
You can try adding

```
Alias /website /home/user/website
```in /etc/apache2/sites-available/website

---

### Post by waloshin on 2010-05-06
Put the web files into /var/www

---

### Post by Demented ZA on 2010-09-09
Found out it was my ISP blocking certain services for "safety". They unblocked these services on my request and voila! my webserver works, aliases and all. Thank you guys for your help though.

---

