---
title: "need help in apache2 using drupal"
date: 2011-07-12
forum: Server Platforms
---

### Post by bx2gp1 on 2011-07-12
scenario:
on pc1 i have windows 7 running xampp and drupal, works perfectly.

on pc2 running ubuntu server 10.04 LTS and separately installed apache2, php5 and mysql5, i can access its index.html when i type the pc2 ip on my pc1 unit using a web browser.

problem:
when i copy and paste my finished drupal folder on /var/www of pc2 and access it on pc1 using a web browser i can only view its home page and when i click on other links like "about us" it will return "not found" while browsing my site on pc1 using pc3 i can access all links, i already modified my dupal settings.php and chmod files folder according to status report of the site but still i cant access other links, any one knows the problem?

---

### Post by bx2gp1 on 2011-07-15
i have found the answer, extract and run this file as root and connect to internet.

> chmod +x install.sh
> ./install.sh

[http://www.drupalcoder.com/files/install.sh_.zip]("http://www.drupalcoder.com/files/install.sh_.zip")

---

