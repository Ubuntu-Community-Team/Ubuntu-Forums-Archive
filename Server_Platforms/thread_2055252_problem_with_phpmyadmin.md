---
title: "problem with phpmyadmin"
date: 2012-09-08
forum: Server Platforms
---

### Post by SeanEE89 on 2012-09-08
At the moment I'm in the process of setting up a web server, and I'm having some trouble with phpmyadmin.  Originally I was getting denied access to it, but now when I put in my localhost/phpmyadmin it's giving me this. Any ideas what I did wrong? haha 

I'm running Ubuntu Server 12.04.1, and when installing I choose the OpenSSH, LAMP and Samba options. I have installed and been able to access webmin successfully. I'm just now having trouble with phpmyadmin. I've been running all this in a virtual machine on virtual box up until now and am having no issues with that, but on this server it just doesn't seem to want to cooperate. :(

I have attached a screenshot of what I'm getting, if including anything else would help please let me know.

---

### Post by shadedpixel on 2012-09-08
This is very odd, how did you go about installing phpmyadmin? You may want to try removing it and installing it again. It seems to work with alot of things. :D

---

### Post by SeanEE89 on 2012-09-08
> **shadedpixel said:**
> This is very odd, how did you go about installing phpmyadmin? You may want to try removing it and installing it again. It seems to work with alot of things. :D

```
sudo apt-get install phpmyadmin
```

when installing I choose the apache option and entered in a password like it requested. 

I uninstalled it with 

```
sudo apt-get remove phpmyadmin
```

Then reinstalled it with the first line I invluded above a few times and it made no difference. Rebooted even and nothing. :\


edit: 

Just ran 

```
sudo apt-get remove phpmyadmin
sudo apt-get purge phpmyadmin
sudo apt-get install phpmyadmin
```

now I'm getting this.

---

### Post by kennethconn on 2012-09-09
What happens when you put in [http://192.168.1.12/phpmyadmin/index.php](http://192.168.1.12/phpmyadmin/index.php)?
What is the contents of /etc/phpmyadmin/apache.conf?

---

### Post by SeanEE89 on 2012-09-09
> **kennethconn said:**
> What happens when you put in [http://192.168.1.12/phpmyadmin/index.php](http://192.168.1.12/phpmyadmin/index.php)?
What is the contents of /etc/phpmyadmin/apache.conf?

Below is the contents of the directory you asked about. when I put in the url you listed I still got the same not found error. I have been running a LAMP server in virtual box up until now, and I just compared the two apache.conf files and they are identical while the virtual box server is working without a hitch.


```
# phpMyAdmin default Apache configuration

Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
        Options FollowSymLinks
        DirectoryIndex index.php

        <IfModule mod_php5.c>
                AddType application/x-httpd-php .php

                php_flag magic_quotes_gpc Off
                php_flag track_vars On
                php_flag register_globals Off
                php_admin_flag allow_url_fopen Off
                php_value include_path .
                php_admin_value upload_tmp_dir /var/lib/phpmyadmin/tmp
                php_admin_value open_basedir /usr/share/phpmyadmin/:/etc/phpmyadmin/:/var/lib/phpmyadmin/
        </IfModule>

</Directory>

# Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
    <IfModule mod_authn_file.c>
    AuthType Basic
    AuthName "phpMyAdmin Setup"
    AuthUserFile /etc/phpmyadmin/htpasswd.setup
    </IfModule>
    Require valid-user
</Directory>

# Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
    Order Deny,Allow
    Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
    Order Deny,Allow

```

---

### Post by trundlenut on 2012-09-09
I came across what appears to be a bug in the phpmyadmin package, not sure if this the same problem, have a look [here]("http://ubuntuforums.org/showthread.php?t=1980715").

---

### Post by iridium191 on 2012-09-09
If your phpmyadmin issue is a show-stopper the maybe you could consider adminer ( [http://www.adminer.org/](http://www.adminer.org/) ).
 
Compared to phpmyadmin it has a tiny footprint with a single file download. It has a web interface and does just about everything we've ever had to do with MySQL. We've found phpMyAdmin to be overkill for most MySQL applications.

---

### Post by SeanEE89 on 2012-09-10
> **trundlenut said:**
> I came across what appears to be a bug in the phpmyadmin package, not sure if this the same problem, have a look [here]("http://ubuntuforums.org/showthread.php?t=1980715").

I'll give this a try when I get home, I hope it works!

---

### Post by SeanEE89 on 2012-09-10
> **iridium191 said:**
> If your phpmyadmin issue is a show-stopper the maybe you could consider adminer ( [http://www.adminer.org/](http://www.adminer.org/) ).
 
Compared to phpmyadmin it has a tiny footprint with a single file download. It has a web interface and does just about everything we've ever had to do with MySQL. We've found phpMyAdmin to be overkill for most MySQL applications.

I'll give adminer a look. I dont HAVE to use phpmyadmin, it's just what I'm use to. lol

---

### Post by SeijiSensei on 2012-09-10
Try moving the phpmyadmin code out of apache2.conf and into /etc/apache2/sites-available/default instead.  Make sure it is inside the <VirtualHost> container tags.  Then restart apache with "sudo server apache2 restart"?  Does that work?

---

### Post by SeijiSensei on 2012-09-11
I just replied to someone in [another thread]("http://ubuntuforums.org/showthread.php?t=2055659") with problems similar to yours.  Does /var/log/apache2/error.log have lines saying Apache cannot find /var/www/phpmyadmin?  If so, it seems to be a function of choosing between apache and lighttpd.

I replicated the steps followed by the other poster and used the tasksel approach described in [this article]("http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/") to install apache, php and mysql.  Then I installed phpmyadmin.  It asked me which web server to use, and I told it apache.  When it was complete, phpmyadmin appears when accessed as [noparse]http://localhost/phpmyadmin[/noparse].  Perhaps you made a wrong choice along the way.  I suggest you once again try purging and reinstalling being careful to choose the apache alternative when it is offered.

If that doesn't fix the problem you could try removing all the LAMP components and starting over, following the approach in the linked article above.

---

