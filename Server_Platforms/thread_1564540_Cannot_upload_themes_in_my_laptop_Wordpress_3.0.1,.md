---
title: "Cannot upload themes in my laptop? Wordpress 3.0.1, Lucid Lynx Desktop, LAMP Server"
date: 2010-08-30
forum: Server Platforms
---

### Post by hannah187 on 2010-08-30
Hi all,
I have already logged this issues at [http://wordpress.org/support/](http://wordpress.org/support/) however yet to receive a response yet. Hoping for better luck here.

I am a very new user of Worpress (Blogging software)so go easy with me please however by saying that I am fairly savy when it comes to Operating systems. 
My aim is to build my first Website in my laptop and then host it somewhere else. I have decided to use Wordpress to do that. 
I am using Lucid Lynx Desktop and had installed latest LAMP server.
Installed and configured Wordpress 3.0.1 and can see my blog under //Localhost/Wordpress in my Laptop.
I am now trying to change the theme hence downloaded some themes from the net. I am now logged in and under Admin Menu 

I am using Appearance tab to upload a new theme. But when I try to do that this is the error message I am getting:

**The uploaded file could not be moved to /var/www/wordpress/wp-content/uploads/**

I tried various ways to solve this problem and even CHMOD to give everyone Read, Write and Execute access to this directory 

but I am still getting this error.
Can someone please help me?

Kind regards

---

### Post by hannah187 on 2010-09-04
can some good Samaritan help plz

---

### Post by arrrghhh on 2010-09-04
So do this: ```
ls -la /var/www/wordpress/wp-content/uploads
``` and show us the output.

It should be owned by www-data:www-data and then chmod to 744.  I have the rest of /var/www own'd by root:root and chmod'd to 744.  That gives user read/write rights and everyone else (group & "other") read-only rights.

The reason for the different ownerships is you really only want your www-data user (which is basically the user that accesses your website) to be able to write to your upload directory.  Everything else in /var/www www-data should only be able to read.  Of course if this site is only residing on your laptop and never hitting the outside internet, these security concerns don't really apply.  Just trying to help with "best practices" :D

---

### Post by hannah187 on 2010-09-04
ahhhhh.. at last some reply..thanks mate... I  had been searching a lot and this is where my actions are reported..

[http://wordpress.org/support/topic/cannot-upload-themes-in-my-laptop-wordpress-301-lucid-lynx-desktop?replies=16#post-1675877](http://wordpress.org/support/topic/cannot-upload-themes-in-my-laptop-wordpress-301-lucid-lynx-desktop?replies=16#post-1675877)

as far as your instruction goes here is the output 

hannah@hannah-laptop:/var/www/wordpress/wp-content/uploads$ ls -la
total 16
drwsrwsrwt 3 hannah    www-data 4096 2010-09-04 16:20 .
drwsrwsrwt 7 hannah    www-data 4096 2010-09-05 09:47 ..
drwsrwsrwt 3 www-data www-data 4096 2010-09-04 16:20 2010
-rwsrwsrwt 1 hannah    hannah      20 2010-09-01 00:02 phpinfo.php
hannah@hannah-laptop:/var/www/wordpress/wp-content/uploads$ 

I do understand about the best practices but have done everything 
chmod -R 7777 to get me going..

cheers

---

### Post by arrrghhh on 2010-09-04
Well chmod'ing to 777 should've given everything full read/write access despite the user/group...

Perhaps there's something going on with Wordpress that I'm not grasping.  Have you tried manually uploading anything to that directory?  Not sure the easiest way to do that... Raw HTTP perhaps, using put.

After reading thru that wordpress support thread, it definitely seems something wordpress-specific.  Perhaps if you install thru aptitude and get rid of all the manual stuff it'll set it up correctly?  You'll need to wipe out any remnants of your manual install before doing the aptitude install.

---

### Post by hannah187 on 2010-09-05
there is some merit in what you are saying though. Let's see. Thanks anyway a lot

---

### Post by hannah187 on 2010-09-05
Please look at this post of mine.. I had changed couple more settings.. still no luck uploading the themes though...

[http://wordpress.org/support/topic/cannot-upload-themes-in-my-laptop-wordpress-301-lucid-lynx-desktop?replies=21#post-1676276](http://wordpress.org/support/topic/cannot-upload-themes-in-my-laptop-wordpress-301-lucid-lynx-desktop?replies=21#post-1676276)

---

### Post by hannah187 on 2010-09-08
Ok some success. I have added this line in wp-config.php and am able to upload some theme files.. 
define('FS_METHOD', 'direct');
Some other theme files are still giving me grief..

More info:

Also added myself in www-data user group

$ sudo usermod -aG www-data hannah

---

### Post by webtechquery on 2011-11-26
A simple and easy solution to this issue could be found in the folloing link:

[http://www.webtechquery.com/index.php/2011/11/wordpress-the-uploaded-file-could-not-be-moved-to-varwww-ubuntu-linux/](http://www.webtechquery.com/index.php/2011/11/wordpress-the-uploaded-file-could-not-be-moved-to-varwww-ubuntu-linux/)

---

