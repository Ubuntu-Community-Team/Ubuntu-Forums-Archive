---
title: "PHP Help"
date: 2009-03-08
forum: Server Platforms
---

### Post by bc040401056 on 2009-03-08
Hi friends,

Im new to ubuntu and im using latest version of it my computer is a client of lan.

I have successfully installed php apache and mysql but when i write a php program in notepad and save it in .php format and when i open that file it shows no out put only the notepad opens can u please tell me which thing is im missing to configure or what i have to do please

---

### Post by drubin on 2009-03-08
php needs to run the file. This is generally done on the command line.
php filename.php

or by viewing it through a web browser, ie [http://localhost/test.php](http://localhost/test.php) if the file is saved in /var/www/test.php this would be the standard install of php/apache.

---

### Post by hyper_ch on 2009-03-09
actually for the cli you need to install the php5-cli package first :)

---

