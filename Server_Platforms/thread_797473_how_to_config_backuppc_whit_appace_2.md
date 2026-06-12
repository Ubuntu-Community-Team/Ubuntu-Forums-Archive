---
title: "how to config backuppc whit appace 2"
date: 2008-05-17
forum: Server Platforms
---

### Post by motio on 2008-05-17
i instal ubunut 8.04 server and backuppc when i tst the appche 2 i get the page whit the masge it works but when i try to run the backuppc nating work tank for any help

---

### Post by Girya on 2008-05-18
This will should work

sudo chmod 777 /etc/apache2/apache2.conf
sudo cat /etc/backuppc/apache.conf >> /etc/apache2/apache2.conf
sudo chmod 644 /etc/apache2/apache2.conf
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start

I was having the same problem as you. I don't why backuppc won't auto configure apache2 but I found this in a post by searching backuppc. it was posted by bgearig. It adds the required lines to the apache config file so apache can find backuppc. 

it worked great after doing this. Kevin

---

### Post by nycjeff on 2008-07-25
yes, thanks for this. It was very helpful.

---

