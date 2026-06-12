---
title: "Connect to remote MYSQL server"
date: 2012-06-12
forum: Server Platforms
---

### Post by Inderpreet Singh on 2012-06-12
Hi,

In my LAN network I have mysql server on centos and I want that the all developers who works on wamp server can connect to the mysql server on centos..these all computers are on same lan network. So how is this possible that the developers can do projects on their local systems using wamp and they can connect to database on centos server ??

---

### Post by kashif_max on 2012-06-12
Hi,
There are two types of accounts that can be created in MySQL. Local and remote.

In your scenario, you have to create a remote user. The syntax is.
```
GRANT USAGE ON *.* TO 'myDatabas'@'%' . . .
```
% sign indicates a remote user...

---

### Post by Inderpreet Singh on 2012-06-12
> **kashif_max said:**
> Hi,
There are two types of accounts that can be created in MySQL. Local and remote.

In your scenario, you have to create a remote user. The syntax is.
```
GRANT USAGE ON *.* TO 'myDatabas'@'%' . . .
```% sign indicates a remote user...

I am not so aware of mysql...can you please explain step by step how to do this?

---

### Post by Cheesemill on 2012-06-12
You also need to set up the MySQL server to allow remote access.
On Ubuntu this is done by editing /etc/mysql/my.conf and changing the line:
```
bind-address = 127.0.0.1
```to:
```
#bind-address = 127.0.0.1
```and then restarting MySQL.
(CentOS may use the file /etc/my.conf instead, I'm not sure as I don't use it).

---

### Post by N0oki3 on 2012-06-15
> **Inderpreet Singh said:**
> Hi,
 So how is this possible that the developers can do projects on their local systems using wamp and they can connect to database on centos server ??
Hello there. Why wouldn't you use it simplified ? if they are using wamp than they actually can have database on their own PC. So instead they could all just access to database normally. (Back in school where we had to do php website developing it was up to 30-60 people at the same time online on the same database)

So. What you have to do. 
install phpmyadmin
```
yum install phpmyadmin
yum install mysql-server
service mysqld start
mysqladmin -u root password PASSWORD_HERE
```


Than edit file
```
vi /etc/httpd/conf.d/phpmyadmin.conf
```

```
<Directory "/usr/share/phpmyadmin">
  Order Deny,Allow
  Deny from all
  Allow from 127.0.0.1
</Directory>
```
Now you can allow from all or allow specified ip's
to finish editing do 
```

press escape button;
:wq 

```

Now access your IP/phpmyadmin and you will get some random error

than on server edit 
```
vi /usr/share/phpmyadmin/config.inc.php
```

> $cfg['blowfish_secret'] = '**yoursecretpassphrase**'; /* YOU MUST FILL IN THIS
FOR
COOKIE AUTH! 


however, if you want phpMyAdmin to connect to a remote server, you can change the line by replacing localhost with your server IP:
```
$cfg['Servers'][$i]['host'] = 'localhost';
```

Under ip/phpmyadmin u can cr8 new users(for sql database), for your developers

**edit** setup ftp server - so they connect with fillezilla:

```

yum install vsftp
vi /etc/vsftpd/vsftp.conf
chkconfig vsftpd on
service vsftpd restart

```

to add people:
```

useradd username
passwd username

```

---

### Post by Habitual on 2012-06-16
> **kashif_max said:**
> ...% sign indicates a remote user...

Incorrect. the % symbol represents **any** remote client.

---

