---
title: "var/www to home/user/public_html"
date: 2011-06-09
forum: Server Platforms
---

### Post by mandza on 2011-06-09
i have one more problem :)
i dont know how to configure apache so it would work from /home/user/public_html i tryed virtualhost but i think that i do something wrong.
if you can send any guide for this i will be very gratefull.

---

### Post by ruffEdgz on 2011-06-09
So, if you still haven't changed much with your apache2 install this should be able to help:
[LIST=1]
[*]Go to /etc/apache2/sites-enabled
[*]Check to make sure that the 'default' site config is there
[*]Edit the 'default' site config (vim ./000-default)
[*]Look for DocumentRoot and change the location to where you would like it to be
[*]Save document and restart service
[*]Make sure the new location can be accessed by the user/group www-data (or to the user that owns the apache service) 
[/LIST]

The 'DocumentRoot' helps define the location for a certain VirtualHost: [http://httpd.apache.org/docs/2.0/mod/core.html#documentroot](http://httpd.apache.org/docs/2.0/mod/core.html#documentroot)

Cheers!

---

### Post by elliotbeken on 2011-06-09
or you could use a symlink ?

---

### Post by memilanuk on 2011-06-09
[http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)

If you need PHP to work, pay particular attention to the link towards the end about enabling PHP for user public_html directories... it is not enabled by default.

---

### Post by mandza on 2011-06-25
> **memilanuk said:**
> [http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file](http://kimbriggs.com/computers/computer-notes/linux-notes/apache2-public_html-virtual-directories.file)

If you need PHP to work, pay particular attention to the link towards the end about enabling PHP for user public_html directories... it is not enabled by default.

Thank your very much it was what i needed. furrEdgz thank you too,

---

### Post by yotam on 2011-06-25
Consider enabling **userdir** module.
Currently it works for me except for cgi-bin.
See [UbuntuForums Configure Apache to enable cgi-bin user directories]("http://ubuntuforums.org/showthread.php?p=10979363#post10979363").

---

### Post by Lars Noodén on 2011-06-25
As mentioned by yotam, [mod_userdir](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html#userdir) may be what you want.  It is very easy to set up.

---

### Post by mandza on 2011-06-27
my server now work like i wanted it to work 192.168.1.18/~mysite/ but i have another problem, my php scripts doesnt run. it directly download my index.php file dont open the site.

---

### Post by Ryan Dwyer on 2011-06-27
Edit /etc/apache2/mods-available/php5.conf and comment the line that says "php_admin_value engine Off". Save and restart Apache.

---

### Post by mandza on 2011-06-27
> **Ryan Dwyer said:**
> Edit /etc/apache2/mods-available/php5.conf and comment the line that says "php_admin_value engine Off". Save and restart Apache.

there is no php5.conf file in /etc/apache2/mods-available folder. :S
-----------------------------------------------
i had run a2enmod and file was come. after that i had comment php_admin_value engine off in php5.conf and when i restart apache2 it was working.
Thanks a lot.

---

