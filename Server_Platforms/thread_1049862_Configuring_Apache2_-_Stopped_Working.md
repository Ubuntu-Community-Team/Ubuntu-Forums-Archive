---
title: "Configuring Apache2 - Stopped Working"
date: 2009-01-25
forum: Server Platforms
---

### Post by PCHome on 2009-01-25
I have configured Apache and Apache2 countless times in Windows but am new at doing it in Ubuntu. On Ubuntu 8.10 non-server version, I had LAMP installed and running well until I tried to add to the configuration so that it would run the local development versions of my Web sites. I am not sure if I am doing in correctly but I need each site to load at [http://sitename/](http://sitename/) rather than [http://localhost/sitename/](http://localhost/sitename/) and, as I was using VirtualHost in Windows, that's what I tried here. For some reason none work and now the Apache2 default site does not load either even though Apache2 itself is running. Can anyone help me with this? Thanks!

Don

---

### Post by R.Bucky on 2009-01-25
To make sure Apache knows what your domain name is, edit your httpd.conf to read ```
ServerName your_domain_name.net
``` You can edit your file in terminal using ```
sudo gedit /etc/apache2/httpd.conf
```Restart apache with ```
sudo /etc/init.d/apache2 force-reload
```You will need to make sure that your /etc/hosts file reflects your domain name as well.

---

### Post by PCHome on 2009-01-25
The httpd.conf file is empty and all configuration appears to be in apache2.conf instead. I used the httpd.conf in Windows but it did not install itself that way here in Ubuntu. Should there be something in httpd.conf to tell it to look at apache2.conf? Thinking that might be the case I added

```
Include /etc/apache2/apache2.conf
```

to httpd.conf but it made no apparent difference,

In any event, rather than appending to it, I added a separate file for each site as /etc/apache2/sites-available/sitename with each containing something like this:

```
<VirtualHost *:80>
ServerAdmin contact@sitename.com
ServerName sitename
ServerAlias sitename
DirectoryIndex index.php
DocumentRoot /var/www/vhosts/sitename
LogLevel warn
ErrorLog /var/www/vhosts/sitename/logs/error.log
CustomLog /var/www/vhosts/sitename/logs/error.log combined
<Directory /var/www/vhosts/itename>
</Directory>
ServerSignature off
</VirtualHost>
```

Should I have done it differently? This is similar to what it had in the Windows httpd.conf file.

Apache2 worked just fine when first installed, however, I think that an earlier attempt to get it working with my sites caused the problem and I'm not sure what it was. I tried reinstalling Apache2 in the hopes of having it go back to the defaults but it did not seem to do so.

(Since my sites are purely local, there are no ".net" or .com". They are just simply sitename.)

Don

---

### Post by PCHome on 2009-01-25
Suddenly it's working! There was a misnamed folder; rather than being at 

```
ErrorLog /var/www/vhosts/sitename/logs/error.log
CustomLog /var/www/vhosts/sitename/logs/error.log combined
```

the folder was "log". I'm not sure if that was enough to stop the others too since they were named properly but correcting it seems to have gotten it all going.

I do not see a /etc/hosts file but there is a /etc/hosts.conf although there is nothing in it specific to these sites. I do recall seeing hosts in a different folder but cannot locate it again at the moment.

Don

---

