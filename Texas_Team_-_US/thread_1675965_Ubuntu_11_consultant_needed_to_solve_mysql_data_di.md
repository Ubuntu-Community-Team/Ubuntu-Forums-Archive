---
title: "Ubuntu 11 consultant needed to solve mysql data directory on raid problem"
date: 2011-01-26
forum: Texas Team - US
---

### Post by drake51 on 2011-01-26
I need help resolving problem of installing mysql on Ubuntu 11 64bit.  I have set up a raid array using four 1TB disks and can not get the mysql server to start after changing the data directory location to the raid volume.  I have tried following all the on line methods to install and change data directory but to no avail.  I have changed permissions, ownerships, etc to be like the /var/lib/mysql data directory.  I have even disabled the apparmor profile for mysql.  
 
I thought that I would reach out to the Ubuntu group in Texas and even someone in Austin.  I will need additional consulting help to set up some web servers using tomcat to push computationally intensive RIA to clients.
 
Hope someone out there can respond soon.
cheers
ken

---

### Post by Druke on 2011-01-26
Howdy!

>  I have tried following all the on line methods to install and change data directory but to no avail. I have changed permissions, ownerships, etc to be like the /var/lib/mysql data directory. I have even disabled the apparmor profile for mysql. 

what did you do to change the data directory?

[Semi related thread?]("http://ubuntuforums.org/showthread.php?t=804126")

---

### Post by gordintoronto on 2011-01-26
Are you trying to run production workload on a beta operating system?  A much better choice would be 10.04 LTS.

---

### Post by Druke on 2011-01-26
Also, for the record: I am an Austin local.

---

