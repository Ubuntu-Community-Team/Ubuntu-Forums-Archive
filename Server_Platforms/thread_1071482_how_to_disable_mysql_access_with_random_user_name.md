---
title: "how to disable mysql access with random user name"
date: 2009-02-16
forum: Server Platforms
---

### Post by tutunmayan on 2009-02-16
Hi I setup an Ubuntu server and PhpMyAdmin on it. Today I discovered that a random username with no password can login to PMA. And can see information_schema database. 
 
How can I fix this? 
 
thank you so much

---

### Post by Phlee on 2009-02-16
> **tutunmayan said:**
> Hi I setup an Ubuntu server and PhpMyAdmin on it. Today I discovered that a random username with no password can login to PMA. And can see information_schema database. 
 
How can I fix this? 
 
thank you so much

Inside the conf file of phpmyadmin you can specify local authentication.  I would do that.  Maybe make it so only sudo'ers or root can login if you don't want users to log.

---

### Post by tutunmayan on 2009-02-17
> **Phlee said:**
> Inside the conf file of phpmyadmin you can specify local authentication.  I would do that.  Maybe make it so only sudo'ers or root can login if you don't want users to log.

Phlee thank you for your reply but I could not understand how to make it. config.inc.php file does not include a clue about local authentication.

---

