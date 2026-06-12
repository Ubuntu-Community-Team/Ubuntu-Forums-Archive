---
title: "Forgot the mysql password....."
date: 2008-12-10
forum: Server Platforms
---

### Post by dj_ee3 on 2008-12-10
Hi, Some days ago I started trying to make a server on my computer. For this goal to happen I install LAMP. Than at first I had problems putting files in my /var/www folder which after a long fight I finally made it to work. But, now here is the other problem. I am not exactly sure but I remember entering a password during the Lamp instalation which I thought is my mysql password but now when when I am trying to install script that I had used before it does not want to connect to mysql. So bacicly I don't have access to my mysql server. Can you tell me a way to change the password of MSQL without knowing the current password? If there is not one can you tell me how to do full uninstall of LAMP so I can start from clean instalation again. Thank you in advice!

---

### Post by bluefrog on 2008-12-10
try that

reset root password
sudo /etc/init.d/mysql stop
sudo /usr/bin/mysqld_safe --skip-grant-tables &
mysql -u root mysql
UPDATE user SET password=PASSWORD('your_password') WHERE user = 'root';
FLUSH PRIVILEGES;
quit;
sudo pkill mysql_safe   (or kill -9 pid)
sudo /etc/init.d/mysql restart

---

### Post by hyper_ch on 2008-12-10
[http://www.cyberciti.biz/tips/recover-mysql-root-password.html](http://www.cyberciti.biz/tips/recover-mysql-root-password.html)

---

### Post by cdenley on 2008-12-10
Easier than that. I think this will work on hardy or intrepid.
```

sudo dpkg-reconfigure mysql-server-5.0

```

If you really want to completely remove it, though
```

sudo dpkg -P mysql-server mysql-server-5.0

```

---

### Post by sundarrajan on 2009-03-07
Yes it worked for me .....

Its really useful ....

Use the command 

sudo dpkg-reconfigure mysql-server-5.0

---

