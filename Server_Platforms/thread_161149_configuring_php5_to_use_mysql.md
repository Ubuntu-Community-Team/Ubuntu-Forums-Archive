---
title: "configuring php5 to use mysql"
date: 2006-04-16
forum: Server Platforms
---

### Post by Gaia on 2006-04-16
hi,

I installed PHP5, MySQL 4.1 and Apache2.  It says that PHP5 doesn't have MySQL enabled by default so i was wondering what I need to edit/do inorder to enable MySQL with PHP5?

Thanks.

---

### Post by gmclachl on 2006-04-16
sudo apt-get install php5-mysql 

 George

---

### Post by Gaia on 2006-04-16
Thanks George.

I seem to have another problem though.  Apache2 seems to be working, but when i go to localhost and click a php file it keeps asking me where i want to save it/open it with rather then just running the actual file.

MySQL seems to work as i can connect using the MySQL Administrator i installed. But PHP won't seem to work...

Any suggestions?

Thanks.

---

### Post by gmclachl on 2006-04-16
Hmmm,  libapache2-mod-php5 is also installed when you get php5. So that should work. 

 Have you tried 
                         sudo a2enmod php5 

 George

---

### Post by Gaia on 2006-04-16
hey,

Thanks, it said that it was installed and that i just needed to force a reload of apache2.

Seems to be working fine now, thanks!

---

### Post by lamorack on 2006-04-24
[QUOTE=gmclachl]sudo apt-get install php5-mysql 

 George[/QUOTE]


Is there any problem using this command in a PHP5+Apache2+MySQL5 environment??

Im not sure, because the command tries to install mysql-common...

Any comment about it? Can mysql-common crash the MySQL5 installation?

Thanks, forum!

---

