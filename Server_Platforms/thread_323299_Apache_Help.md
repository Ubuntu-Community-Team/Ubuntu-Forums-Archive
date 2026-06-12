---
title: "Apache Help"
date: 2006-12-21
forum: Server Platforms
---

### Post by white_tiger_daniel on 2006-12-21
Hey there.  I have a small problem.

When I type in 'localhost' in firefox to test my apache, it works.  But when I try to access any php stuff e.g. phpmyadmin or phpBB it asks me if I want to open or save the PHP file.  What can I do to stop this madness ](*,) ?

---

### Post by chrisfay on 2006-12-21
Do you actually have PHP installed?

---

### Post by UCAP on 2006-12-22
Have a look here: [https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031-3](https://help.ubuntu.com/community/ApacheMySQLPHP#head-6ce180906ddbc141ef4b213f82465515a8ad3031-3)

---

### Post by tturrisi on 2006-12-22
put your php files in the correct dir, either /var/www/ or ~username/public_html/

access in browser using [http://localhost](http://localhost) or [http://localhost/~username](http://localhost/~username)

---

### Post by white_tiger_daniel on 2006-12-22
> **tturrisi said:**
> put your php files in the correct dir, either /var/www/ or ~username/public_html/

access in browser using [http://localhost](http://localhost) or [http://localhost/~username](http://localhost/~username)

Yeah, they are..

---

### Post by white_tiger_daniel on 2006-12-22
> **chrisfay said:**
> Do you actually have PHP installed?

Yup

---

### Post by tturrisi on 2006-12-22
sudo apt-get libapache2-mod-php5  (may already have it but not yet enabled so continue)
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

---

