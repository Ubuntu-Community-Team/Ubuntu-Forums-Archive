---
title: "Hosting WordPress on my own server - permissions"
date: 2012-03-26
forum: Server Platforms
---

### Post by OliverHaslam on 2012-03-26
Hi guys,

I wasn't sure where best to put this - it's a bit Ubuntu, a bit web hosting - so it's going here because it seems the most active forum!

I've been playing around with setting a web server up on my Ubuntu server which appeared nice and simple. Bored last night, I decided to shove WordPress on there, too.

This is where all kinds of issues began, mainly surrounding NAT and trying to access the site from both outside and inside my network. I've sussed that by editing my local hosts file to point to an internal IP when WordPress tries to load an external one. That's not really the point of this post.

What I am concerned about is permissions.

The site is currently living in /var/www/wordpress, meaning it is accessible from my ip/wordpress, which works fine by me. I'm going to look at getting the required files into /var/www so it loads on the root URL without having to move the entire site there, but again, that's not really the point.

In order to get media to upload to the site I have had to change permissions on the dir structure to 777 which is what a site told me to do after some Google-fu. That's got things working as they should, but being a bit of a permissions n00b that's got me wondering what it has actually done. Some more Googling tells me that wasn't the best thing to do, but I confess to not really knowing why.

So, any WordPress/Linux peeps care to educate me this warm Sunday evening?

Cheers!

---

### Post by nsnidanko on 2012-03-29
> **OliverHaslam said:**
> Hi guys,

...

The site is currently living in /var/www/wordpress, meaning it is accessible from my ip/wordpress, which works fine by me. I'm going to look at getting the required files into /var/www so it loads on the root URL without having to move the entire site there, but again, that's not really the point.



You can modify /etc/apache2/sites-available/default

and change **DocumentRoot /var/www**
to
[B]DocumentRoot /var/www/wordpress

[/B]Without moving your site and it will be accessible by [http://server_ip](http://server_ip) instead of [http://server_ip/wordpress](http://server_ip/wordpress). In WP general settings adjust WordPress Address (URL) and you are set.


> **OliverHaslam said:**
> 
In order to get media to upload to the site I have had to change permissions on the dir structure to 777 which is what a site told me to do after some Google-fu. That's got things working as they should, but being a bit of a permissions n00b that's got me wondering what it has actually done. Some more Googling tells me that wasn't the best thing to do, but I confess to not really knowing why.

So, any WordPress/Linux peeps care to educate me this warm Sunday evening?

Cheers!

777 grants everyone access to these files and directories which is a horrible idea. My guess is that you uploaded files under a different user than what webserver runs as (www-data by default) thus resulting in errors.

 Do the following:
All directories should be 755 or 750.
All files should be 644 or 640. Exception: wp-config.php should be 600

Next issue the following 2 commands to change owner and group
[B]
chown -R www-data /var/www
chgrp -R www-data /var/www[/B]

Cheers,
Naz

---

### Post by OliverHaslam on 2012-03-29
> **nsnidanko said:**
> You can modify /etc/apache2/sites-available/default

and change **DocumentRoot /var/www**
to
[B]DocumentRoot /var/www/wordpress

[/B]Without moving your site and it will be accessible by [http://server_ip](http://server_ip) instead of [http://server_ip/wordpress](http://server_ip/wordpress). In WP general settings adjust WordPress Address (URL) and you are set.




777 grants everyone access to these files and directories which is a horrible idea. My guess is that you uploaded files under a different user than what webserver runs as (www-data by default) thus resulting in errors.

 Do the following:
All directories should be 755 or 750.
All files should be 644 or 640. Exception: wp-config.php should be 600

Next issue the following 2 commands to change owner and group
[B]
chown -R www-data /var/www
chgrp -R www-data /var/www[/B]

Cheers,
Naz

Thanks for the replies.

Will those new permissions allow the uploading of images etc, and will new files automatically receive the required permissions? I obviously want to be able to add posts and images remotely.

Cheers.

---

### Post by nsnidanko on 2012-04-03
yes they should. I don't recall exact architecture of wordpress but there might be some folders for cache and temp files that require 777 but dont quote me on this. Change user and group and give it a try to make sure everything works.

---

