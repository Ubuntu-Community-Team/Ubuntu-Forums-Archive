---
title: "wordpress problems &amp; a request 4 jquery package"
date: 2011-05-13
forum: Server Platforms
---

### Post by boblizar on 2011-05-13
can we get the jquery package to add
```
Alias /jquery.js /usr/share/javascript/jquery/jquery.js
```
to the file /etc/apache2/conf.d/javascript-common.conf to make the jquery ubuntard friendly for the w3c examples/tutorials

k word press doesnt have a /etc/apache2/conf.d/ configuration file nor does it setup a database on mysql, nor does it alias a directory 4 apache.

as my friend [http://www.autosectools.com/](http://www.autosectools.com/) pointed out phpmyadmin is not safe...  my solution to enable and disable phpmyadmin is to comment the alias in /etc/apache2/conf.d/phpmyadmin.conf

```
# phpMyAdmin default Apache configuration

#Alias /phpmyadmin /usr/share/phpmyadmin
```

adding the # sign.  the wordpress tarball is 10 times easier to install than the synaptic version, i find something wrong with this entire situation as the wordpress tarball only takes 10 minutes to get running.

as stated in previous posts i make a ~/web/www directory && sudo mv /var/www/index.html /home/$USER/web/www && ln -s /home/$USER/web/www /srv/www && rm -rf /var/www && sudo ln -s /srv/www /var/www

then that sequence sets the web directory to look for index.html or index.php in ~/web/www and you can set the permissions of those files to a lowly user and apache will serve my garbage to the masses.

---

