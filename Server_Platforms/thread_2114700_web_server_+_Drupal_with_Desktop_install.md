---
title: "web server + Drupal with Desktop install"
date: 2013-02-10
forum: Server Platforms
---

### Post by ieee488 on 2013-02-10
I want to try out Drupal on this old laptop which has Ubuntu 12.04 LTS installed.

I installed Apache2, PHP5, and MySQL per [http://funwithlinux.net/2012/05/ubuntu-12-04-web-server/](http://funwithlinux.net/2012/05/ubuntu-12-04-web-server/) and all went smoothly.

I created a directory /var/www/drupal and copied all the Drupal files there.
Created the database for Drupal and that went smoothly.

But when I run the install script, nothing happens.
I am typing**[http://localhost/drupal/install.php](http://localhost/drupal/install.php)**

Any ideas on what I am doing wrong?

---

### Post by tgalati4 on 2013-02-10
What version of Drupal and is it compatible with 12.04?

I usually use tasksel to install LAMP and don't do any configuration.  Then copy the Drupal files and run the Drupal installer.  It's possible that following the configuration in the link you posted borked the Drupal install.

Did you set the ownership of /var/www to www-data:www-data?

Look in /var/log/apache2 for errors.

Did you increase the memory footprint in /etc/php5/php.ini?

---

### Post by koenn on 2013-02-11
> **tgalati4 said:**
> 

Did you set the ownership of /var/www to www-data:www-data?


iirc, drupal requires a handful of rather specific permissions on the drupal folder and some subdirectories thereof, and on the files in them. 
It's documented on the drupal website

> 
But when I run the install script, nothing happens.
Nothing ?
You'd either get an error from apache (not found, forbidden, whatever), or from the drupal scripts. "Nothing" is highly unlikely. 

Ad what happens if you browse to [http://localhost/drupal/](http://localhost/drupal/)  ?

---

### Post by ieee488 on 2013-02-11
When I browse to [http://localhost/drupal](http://localhost/drupal)   I get a blank web page.

It seems that Drupal expects to be in the web server's root directory. Numerous pages on the web about trying to install Drupal to a subdirectory.

It shouldn't be a big deal to have Drupal be in a subdirectory for some reason for this software it is a big deal.

---

### Post by mizzle00 on 2013-02-11
Hello, thanks for visiting my site.

Check the output of apache's error log at /var/log/apache2/error.log

If you're on an 'older' machine and don't have much RAM, you might not have enough PHP memory in your php.ini file.

I don't know what the minimum for Drupal is off the top of my head, but look for the variable
memory_limit in /etc/php5/apache2/php.ini
and set it to = 128M

If all else fails, consider making a hello world file in php in another directory.

Update:  [http://drupal.org/node/207036](http://drupal.org/node/207036) says minimum php5 memory limit is 32mb.  Since you're just running a site for testing purposes, you should be able to set it as high as you want, but 32mb is the minimum.

---

