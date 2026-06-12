---
title: "phpmyadmin directory in apache2"
date: 2006-10-04
forum: Server Platforms
---

### Post by gu014 on 2006-10-04
Hello,
i am trying to install apache2 and phpmyadmin. both are installed but, when i click the 'phpmyadmin' directory from 'localhost' is asks if i would like to download a .phtml file. when i click on the 'apache2-default' directory i am taken to the correct location.  could anyone help me out with this. thank you very much.

---

### Post by az on 2006-10-04
Be sure you have libapache2-mod-php5 is installed.  That is assuming you are running php5.

See:
[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

and 
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by tytus on 2006-10-25
This happens to me too when I use localhost as URL. However, everything works fine if I use 127.0.0.1 or IP address of my box instead. Hope this helps.

---

