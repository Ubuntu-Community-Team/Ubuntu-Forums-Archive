---
title: "mysql folder permissions changed"
date: 2012-03-26
forum: Server Platforms
---

### Post by britebyte on 2012-03-26
Hello Everyone,

First post here at Ubuntu forums. I have used Debian and Ubuntu on and off for a few years for internal servers but nothing too complicated.

I am setting up a test server for a Drupal and Civicrm installation using Ubuntu server 11.10. Last week I created the Drupal database, made grants for a new user for Drupal, installed Drupal, etc. All worked fine. This week I started on the civicrm part. I created the database using mysqladmin, then went to grant a new user permissions on the civicrm db and got a mysql error 1036 that the user table is read only. I have read a few threads about the error and sure enough the issue it that the /var/lib/mysql/mysql folder is owned by root and not the mysql user. I can go ahead and chown  -R mysql:mysql /var/lib/mysql/mysql.

The real question though is why would this have changed since last week? It was working then. Are these permissions default for an Ubuntu install and something else has changed?

One of the old threads: [http://ubuntuforums.org/showthread.php?t=638999](http://ubuntuforums.org/showthread.php?t=638999)

Appreciate any theories you have on what may have gone wrong.

---

### Post by britebyte on 2012-03-26
I have marked this as solved since there is a good chance I did this myself. I was changing permissions for the Drupal "files" folder. To me my history of commands looks OK but I bet I messed up. I will reinstall this server soon since some other folders in /var have lost their permissions.

"Never ascribe to malice that which can be explained by incompetence."

---

