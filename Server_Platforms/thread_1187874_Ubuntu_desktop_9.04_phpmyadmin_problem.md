---
title: "Ubuntu desktop 9.04 phpmyadmin problem"
date: 2009-06-15
forum: Server Platforms
---

### Post by tcpa41 on 2009-06-15
After running sudo apt-get install php5 mysql-server apache2 phpmyadmin and the adding a  symbolic link sudo "ln -s /usr/share/phpmyadmin/ /var/www/phpmyadmin"
i cant load up phpmyadmin in firefox,when trying to enter localhost/phpmyadmin firefox prompts me to download some sort of phtml file. Any ideas on how to fix this?

---

### Post by ActiveFrost on 2009-06-15
Symbolic link to /var/www/ .. mhh, first time when I hear this !


Open your terminal and :
```
sudo gedit /etc/apache2/apache2.conf
```
Add this line :
```
Include /etc/phpmyadmin/apache.conf
```
Restart apache :
```
sudo /etc/init.d/apache2 restart
```

Enjoy :D

---

