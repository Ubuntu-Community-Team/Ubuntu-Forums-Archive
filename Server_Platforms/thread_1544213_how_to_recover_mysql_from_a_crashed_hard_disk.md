---
title: "how to recover mysql from a crashed hard disk"
date: 2010-08-02
forum: Server Platforms
---

### Post by rejuvenate on 2010-08-02
hi
my server got crashed due to some power glitch i am somehow able to get the access to the /var folder i have copied all my webpages to a  new system from /var/www folder, and i have install LAMP server but still i am not able to access the database from phpmyadmin.
i have copied the database to /var/lib/mysql..
in phpmyadmin it has initially given there is no data base when i replaced the mysql folder but now after a restart it is giving me #2002 cannot log in to the mysql server
even undoing the things is giving me the same error... 
i m not getting wat is wrong

---

### Post by ruffEdgz on 2010-08-02
When you copied over the /var/lib/mysql/... directory that you recovered to the new system, did you make sure the directory ownership was correct (so a chown of /var/lib/mysql to make sure its owned by the right UID and GID)?

After placing in the /var/lib/mysql/... directory, did you restart any of the services to make sure they worked ok (service mysql restart, service phpmyadmin restart, etc...)?

It seems like it can be done but I haven't done this myself because I perform mysqldumps for my backups (site is a person trying to use old /var/lib/mysql/... on new mysql install) : [http://www.webhostingtalk.com/showthread.php?t=670578](http://www.webhostingtalk.com/showthread.php?t=670578)

== FYI ==

Take a look at this thread as someone had something similar to your scenario: [http://ubuntuforums.org/showthread.php?t=1539514](http://ubuntuforums.org/showthread.php?t=1539514)

---

