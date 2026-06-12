---
title: "Installing SuPHP"
date: 2010-06-23
forum: Server Platforms
---

### Post by majdi on 2010-06-23
Hi,

I recently installed ubuntu 10.04 LTS Desktop. I will be using this install as a web development environment, so I installed LAMP and phpMyAdmin using the following;

```
$ sudo apt-get install lamp-server^
$ sudo apt-get install libapache2-mod-auth-mysql phpmyadmin

```

Tested apache, mysql, php and phpMyAdmin and all was working fine until I installed suphp using the following;

```
$ sudo apt-get install libapache2-mod-suphp
```

After the suphp install, I disabled mod_php5 using the following;

```
$ a2dismod php5
```

Then I enabled suphp globally for Apache by editing /etc/apache2/apache2.conf and adding the following at the end of the file;

```
# Enable SuPHP
suPHP_Engine on
suPHP_AddHandler application/x-httpd-php .php
```

Then restarted apache using the following;

```
$ /etc/init.d/apache2 restart
```

Apache is working, but I think the suphp install broke php. When I run my php test script using the following in a text file named testing.php placed in the root folder /var/www;

```
<?php phpinfo(); ?> 
```

I get a 500 Internal Server Error, but php was running fine before the suphp install.

Anyone got this working or can help me fix this, please do.

---

### Post by Ryan Dwyer on 2010-06-23
The libapache2-mod-suphp package doesn't conflict with PHP, so I'd say you need to have PHP enabled. In fact, it depends on suphp-common which depends on either php4-cgi or php5-cgi.

Enable mod_php5, restart Apache, try again, and if you still get a server error check your error log (/var/log/apache2/error.log).

---

### Post by majdi on 2010-06-23
Thanks Ryan,

I enabled php5 using;

```
$ a2enmod php5
```

Now the LAMP install seems to be working fine, but suphp dose not seem to be working. 

Any idea?

---

### Post by Ryan Dwyer on 2010-06-23
I've never used it, so unfortunately I can't help you there.

Read through some of the documentation here ([http://www.suphp.org/DocumentationView.html?file=apache/INSTALL](http://www.suphp.org/DocumentationView.html?file=apache/INSTALL)) about configuring. If you're still having problems check Apache's error log at /var/log/apache2/error.log.

---

### Post by majdi on 2010-06-24
Thanks again Ryan,

The suphp installation notes say;

> Please note that mod_suphp was developped for Apache 1.3.2x and Apache
2.0.x. It might not work with other version.


But I'm running Apache/2.2.14 (Ubuntu). Any other solution or alternative mod that can do the same job?

Anyone???

---

### Post by Ryan Dwyer on 2010-06-24
If the purpose of this is to allow your webserver to run scripts with elevated privileges, you can set that in your /etc/sudoers file. You can tell it to only run certain commands as root so it's much better than giving it full access.

If that's the sort of setup you want I can get you the information I used in /etc/sudoers so you can change it to your needs.

---

### Post by majdi on 2010-06-26
Thanks again Ryan,

Yes that is the idea, because I will be running a CMS which runs PHP scripts and when installed in ver/www the owner and group is root, so the CMS is not able to run the scripts due to the permissions issue. I know suphp will solve this problem, but cant get it to work.

It sounds like your solution is a better option, never attempted such an option, so I will need help in configuring it.

Thanks again.

---

### Post by Ryan Dwyer on 2010-06-26
In that case I recommend setting the group to www-data on all your files in /var/www, then giving group write access.

chgrp -R www-data /var/www
chmod -R g+w /var/www

Your CMS should then have full write access to the /var/www folder.

---

### Post by majdi on 2010-06-26
Thanks Ryan,

That worked just fine. Is there a way I can make these setting permanent for any files/folders added to /var/www?

---

### Post by Ryan Dwyer on 2010-06-26
Any new files and folders added by www-data will have the user set to itself so it will be able to write to those files fine. If you make a new file there yourself you will need to chgrp/chmod it.

---

### Post by Vegan on 2010-06-27
When I installed my server I used tasksel from the installer and I was up almost instantly.

Never needed to muck with anything.

---

### Post by cordoval on 2010-11-03
For the sake of others that may be tempted to follow a change of group or chmod on the files/folders, do not!

This is what I posted on the suphp mailing list, perhaps you can learn from my experience, I spent weeks on this:


Great I was able to solve it, and it seems to be executing now suphp as the /var/log/suphp/suphp.log is filling up
I feel so good, after weeks of trying this it is so encouraging.
I commented the line from my apache.conf

# Enable suPHP
#LoadModule suphp_module /usr/lib/apache2/modules/mod_suphp.so
#AddType application/x-http-php5 .php
suPHP_Engine on
suPHP_AddHandler application/x-httpd-php .php

What I have to say is:

1- ubuntu apache2 already loads the suphp_module by itself, i don't need to add the LoadModule line
2- commenting the line AddType ... php5 is what made the difference as it was in my opinion telling apache to interpret the php with the module php5 which was already disabled
3- suPHP_Engine on was right and the place is perfect as I need it globally on and not just on one virtual host
4- suPHP_AddHandler application/x-httpd-php5 was turned into php alone as I think the php5 is related to the php5 module and I had disabled this, however, I have not tried this as an isolated change besides 2

Other notes:
- I have noticed that most of the frustration was due to the fact that I needed to shut down and restart chrome and I was not doing that, I was only cleaning the cache and that was not enough to see the changes
- There was nothing that I needed to do in terms of cgi settings, not even one change
- file to change configuration for suphp is /etc/suphp/suphp.conf
 and not /etc/apache2/mods-available/suphp.conf as I was told

I was badly treated on the IRC channels #httpd, #php, and #phpc
sadly very proud people (not everybody) from bigger companies that are there to display their pomp. There are very great helpers though. They still hang in there from time to time.

Finally solved.

---

