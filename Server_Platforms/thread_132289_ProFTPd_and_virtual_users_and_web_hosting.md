---
title: "ProFTPd and virtual users and web hosting"
date: 2006-02-18
forum: Server Platforms
---

### Post by stein on 2006-02-18
Hi everyone,

I have a Ubuntu 5.10 server running Apache2 and Proftpd

I have set up some websites as follows w/Apache2 using virtual hosts

/var/www/website1/
/var/www/website2/
/var/www/website3/

I now want to create virtual users in ProFTPd and give them access to the above sites for my users so that they can manage their website files...

I'm having trouble with permissions, file ownership, and chrooting...

ISSUE: Both apache2 and the virtual users need to be able to create/modify/delete files in the "/var/www/website1", "/var/www/website2", etc
directories... And so far, I have been unable to figure out how to get that to work :-(

1) What user:group ownership should the /var/www/websitex directories and their subdirectories and files be set to?

2) What would a skeleton <Directory> entry in proftpd.conf look like for one of the above website directories, "/var/www/website1" for example?

3) i'm currently using custom authfiles to store the virtual users and virtual groups... is this part of the problem? should i be storing them in mySQL instead?

---

### Post by stein on 2006-02-19
ok... [sheepish grin]

i guess i should have done a simple google search for the terms "proftpd mysql"...

came up with the following VERY helpful tutorial:

[Proftpd, mysql, and virtual users tutorial]("http://www.howtoforge.com/proftpd_mysql_virtual_hosting")

---

