---
title: "can't connect to MySQL or login with root"
date: 2018-12-01
forum: Server Platforms
---

### Post by cazz on 2018-12-01
hi
After I have install and upgrade to 18.04 I did then install MySQL and run the security installation
but I can't login to the MySQL with the password it just say "Access denied for user 'root'@'localhost'


I have run the security installation and even reboot the server but still I can't login


/UPDATE

Did find I have to use this

[HTML]sudo mysql -u root[/HTML] and then set a password

---

### Post by bill-lancaster on 2019-01-30
Hello Caz, I have the same problem.
```
sudo mysql -u root
```
takes me straight into mysql( I get 'mysql>' prompt)
How did you proceed to change the password?

---

### Post by LHammonds on 2019-02-02
If AppArmor is installed and running, make sure it is configured for your database.

---

### Post by hgkrug1 on 2019-02-16
I also had many problem with both mysql and mariadb (ubuntu 18.04). I could not get mariadb to work. I both using instructions at [https://stackoverflow.com/questions/50573787/how-to-forcefully-remove-mysql-and-mariadb-from-ubuntu-16-04-without-apt-get](https://stackoverflow.com/questions/50573787/how-to-forcefully-remove-mysql-and-mariadb-from-ubuntu-16-04-without-apt-get) 

$ dpkg --list|grep -i mysql 
and 
$ dpkg --list|grep -i mariadb

$ dpkg -remove --force-remove-reinstreq <package-list>

Then installed mysql as described at [https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/](https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/) 

Works well now, even after reboot. Don't know why this solution is not more widely spreaded!

---

