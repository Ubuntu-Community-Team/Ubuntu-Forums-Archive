---
title: "Munin: Apache server-status returning 404, then redirecting to my Wordpress install"
date: 2013-01-13
forum: Server Platforms
---

### Post by OliverHaslam on 2013-01-13
I'm trying to get Munin's various Apachie plugins to work on my web server, but I'm hitting issues. Upon asking Munin to check available plugins, two of the three Apache plugins return an error saying that "apache server-status cannot be found.'
I've got mod_status turned on etc, and as far as I know, everything's set up correctly.
I've tried opening localhost/server-status using Lynx, at which point I get a 404 error and my Wordpress error page is shown (the one you get when you try to access a page that doesn't exist.)
Now presumablty this is something to do with how I have Apache serving a Wordpress install etc. The web site lives in /var/www/wordpress, with the Index.php file one level up and the .htaccess file amended as per the Wordpress instructions. It works fine, but I've a niggling feeling that when Munin/Lynx tries to load localhost/server-status, it's looking for it in /var/www/.....
So, how do I tell Apache where to actually look when requesting server-status?
Cheers.

---

### Post by chrisguk on 2013-01-14
Hi,

First of all I think your question regarding apache server would be better suited in an Apache server forum or PHP related because this type of questions pop up all the time.

I would like to firstly focus on the index.php file being one level up.  In the real world this is not an ideal setup.  Will wordpress be the only application running on your website?

If it is then there is no reason for it not to be setup as the default installation suggests.  Are you running Wordpress on a local machine for testing?

If you are then why not create a virtual host and have the document root set to /var/www/wordpress or a name of your choosing.  It will be far easier to administer if you decide to install other blogs/websites/forums etc 

There are literally hundreds of tutorials on google that explain how to setup virtual hosts.

If you have anymore questions then please feel free ;)

---

### Post by OliverHaslam on 2013-01-14
> **chrisguk said:**
> Hi,

First of all I think your question regarding apache server would be better suited in an Apache server forum or PHP related because this type of questions pop up all the time.

I would like to firstly focus on the index.php file being one level up.  In the real world this is not an ideal setup.  Will wordpress be the only application running on your website?

If it is then there is no reason for it not to be setup as the default installation suggests.  Are you running Wordpress on a local machine for testing?

If you are then why not create a virtual host and have the document root set to /var/www/wordpress or a name of your choosing.  It will be far easier to administer if you decide to install other blogs/websites/forums etc 

There are literally hundreds of tutorials on google that explain how to setup virtual hosts.

If you have anymore questions then please feel free ;)

Posted to serverfault.com too, but thought the nice people on here may have some ideas too :)

Originally, I installed Wordpress in /wordpress before I really knew what I was doing. When I wanted the site to be accessible via the root URL rather than /wordpress, the web suggested the solution I have now, which is have index.php in / and have .htaccess know that the rest of the content is in /wordpress. Since then, another site has been installed that uses vhosts properly. Well, I say properly.....it works :)

Think the best course of action is to reverse that?

---

