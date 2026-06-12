---
title: "Unable to connect to localhost"
date: 2012-02-08
forum: Server Platforms
---

### Post by cancelledczech on 2012-02-08
Yesterday I installed a LAMP server set-up on my laptop to play around with Drupal and Wordpress locally. Everything installed well and I was able to access myphpadmin and work on a wordpress site on my computer.

I had an issue with wordpress wanting FTP credentials before it would update modules and I followed a couple of tutorials to fix the issue. I used "sudo chown -R www-data /var/www/wordpress/" and added "define(‘FS_METHOD’, ‘direct’);" to my wp-config.php file. That fixed the problem and I was able to play around on my test site.

When I was done playing for the day, I used sweeper to clean up (normal habit after surfing) and turned off the computer. Today when I went to go to my site and learn some more stuff, I was unable to connect to the localhost. Firefox comes up with a page loading error and says that it cannot connect to the server at localhost. I tried typing in 127.0.0.1 and that gave the same connection error.

Obviously I monkeyed something up yesterday, but I have not a clue as to what. I am still learning about Ubuntu and would say that I am a novice user. I have a fresh install of 11.10 and manually installed Apache 2, mySQL, and PHP yesterday. The install seemed to go fine.

Any ideas on what I messed up? Firefox connects out to other sites without a problem (I am on that computer now).

Thanks for any help.

---

### Post by SeijiSensei on 2012-02-08
Did you try restarting the HTTP server with the command "sudo service apache2 restart"?

---

### Post by cancelledczech on 2012-02-08
You totally rock! Using the restart command let me know that I had a bad username written in the apache file. I forgot that I had tried changing that yesterday when I was fixing the file permission issue. I went in and changed the name back to what it should be and then restarted apache. I am able to get to my site now. Thanks a ton!

---

