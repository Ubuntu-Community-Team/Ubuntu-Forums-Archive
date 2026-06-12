---
title: "Accessing phpmyadmin remotely"
date: 2015-04-12
forum: Server Platforms
---

### Post by Xiah on 2015-04-12
I've got a 3 servers & 1 windows machine running in a LAN
HTTP server (Apache2, PHP5 & phpmyadmin) - 10.0.0.10
DNS - 10.0.0.1
MySQL - 10.0.0.40
Windows - 10.0.0.157
 
I'm currently trying to access phpmyadmin from the windows machine using 10.0.0.10/phpmyadmin, which works fine and dandy. However here comes the issue.

If I try to login as normal with the user/password that was set up on the original install of phpmyadmin I get ```
#2002 Cannot log in to the MySQL server
``` at the top and ```
Connection for controluser as defined in your configuration failed.
``` at the bottom of the php login script.

So I decided to do abit of digging and found that in ```
/etc/phpmyadmin/confi.inc.php
``` there are two lines (below) that if coded out will allow to login. 
```

$cfg['Servers'][$i]['controluser'] = $dbuser;
$cfg['Servers'][$i]['controlpass'] = $dbpass;

```
And adding 

```
/etc/phpmyadmin/apache.conf

Order Deny, Allow
Deny from all
Allow from 127.0.0.1
Allow from 10.0.0.157

```

This solves the latter error code, but I still get. ```
#2002 Cannot log in to the MySQL server
```

Further digging and I found that adding the below into may solve the issue. ```
/etc/phpmyadmin/conf.inc.php
```

```
$i++;
$cfg['Servers'][$i]['host'] = 'HostName:port'; //provide hostname and port if other than default
$cfg['Servers'][$i]['user'] = 'userName';   //user name for your remote server
$cfg['Servers'][$i]['password'] = 'Password';  //password
$cfg['Servers'][$i]['auth_type'] = 'config';       // keep it as config
```

Now i'm given a drop down menu of "server choice" of where i'd like to log in which is the hostname/port of the above mentioned, however I get the following if i chose that option.
```
#2005 - Unknown MySQL server host 'raspberrypi:3306' (0)
phpMyAdmin tried to connect to the MySQL server, and the server rejected the connection. You should check the host, username and password in your configuration and make sure that they correspond to the information given by the administrator of the MySQL server.
```

I tried changing the hostname to a different machine and tried logging in that way, however still the same issue remains. 

My final goal is to be able to access the phpmyadmin site and do whatever I need to do via the windows machine. I also have everything configured correctly to use mysql on the HTTP server.

I've tried looking around for some more information but i've came to a brick wall. Does anyone have any suggestions? :-(

---

### Post by SeijiSensei on 2015-04-12
1)  The MySQL package is usually configured to listen only on localhost for security.  You need to edit my.cnf and set "bind-address=*" so it will listen on all interfaces.  Then run "sudo service mysql restart" to restart the server.

2)  MySQL users include both a username and a location.  To connect from a remote machine, the username must exist in the server's authentication database as 'username'@'%' with the '%' representing any remote client's hostname.  To limit logins with that name to a specific client IP address, like the machine running phpmyadmin, use 'username'@'ip.addr.of.client', like 'john'@'10.1.1.1'.

---

### Post by Xiah on 2015-04-12
Thanks for the reply Seiji, i've tried both commenting out the bind-address, setting it to 0.0.0.0 and * but still the same issue.

I've got the mysql server users such as 'https'@'10.0.0.10' and 'https'@'localhost', but still no joy :(

---

### Post by cariboo on 2015-04-12
Check to see if port 3306 on your MySQL server is open to the rest of your local network.

---

### Post by SeijiSensei on 2015-04-12
One quick test is to run "telnet ip.addr.of.server 3306" and see if the server replies.

---

### Post by Xiah on 2015-04-14
I did manage to fix it. From a basic install these are the steps to allow remote connection. Incase anyone else ever needs it

#1 Code out in
/etc/phpmyadmin/confi.inc.php
$cfg['Servers'][$i]['controluser'] = $dbuser;
$cfg['Servers'][$i]['controlpass'] = $dbpass;


#2 Edit
/etc/phpmyadmin/apache.conf
Order Deny, Allow
Deny from all
Allow from 127.0.0.1
Allow from 10.0.0.157   (This is the machine you want to access the myphpadmin website from)


#3 Edit and change
/etc/my.cnf 
bind-address = 0.0.0.0 (This allows any machine on the network to connect to the mysql)


#4
edit
/etc/phpmyadmin/config.inc.php
put add at the bottom

$i++; 
$cfg['Servers'][$i]['host'] = '10.0.0.40'; //mysql server IP 
$cfg['Servers'][$i]['user'] = 'username'; (username you want to log into 10.0.0.10/phpmyadmin) (10.0.0.10 is the server that has phpmyadmin on)
$cfg['Servers'][$i]['password'] = 'password'; //password 
$cfg['Servers'][$i]['auth_type'] = 'config'; // keep it as config



This allows me to log in on my windows machine with the IP 10.0.0.157 in a web browser with 10.0.0.10/phpmyadmin with the username/password combo as above.
  When 10.0.0.10/phpmyadmin is accessed, this drop down menu is the addition are given with #4
  

[IMG]http://i.imgur.com/AdApdo5.jpg[/IMG]

---

