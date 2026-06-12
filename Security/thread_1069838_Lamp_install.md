---
title: "Lamp install"
date: 2009-02-14
forum: Security
---

### Post by menschtx on 2009-02-14
Two part question: 
When after going thru an install of lamp-for the snort install. Then trying sudo /etc/init.d/apache2 restart I get a message  Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
I then went back and attempted bind address = my ip address, bind-address - command not found. Then with $ mysql -u root I get the  Access denied for user 'root'@'localhost' (using password: NO)
At help.ubuntu.com/ mysql password reset, the instructions talk about disabling networking - now does this mean disconnect from the internet? I at this time have no other pc. Lastly how do I bind the address to my ip address?

---

### Post by cariboo on 2009-02-14
You should worry about the 

> Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

I won't any difference to the operation. If you do want to fix it just set up and alias in /etc/host eg:

```
192.168.1.200  myserver
```

The command you want for mysql is:

```
mysql -u root -p
```

Enter the password you setup when you install mysql.

If you don't remember the mysql password, the easiest way to reset it is to run:

```
sudo dpkg-reconfigure mysql-server-5.0
```

When a howto tells you to disable networking type:

```
sudo /etc/init.d/networking stop
```

to restart it type:

```
sudo /etc/init.d/networking start
```

Jim

---

### Post by menschtx on 2009-02-21
Is it possible to uninstall the mysql - the security seems to have stopped firefox 3, I have since installed Arora.

---

### Post by cariboo on 2009-02-21
Mysql or security settings have nothing to do with firefox not running. You have other problems. I would suggest you back up your bookmarks then delete ~/.mozilla/firefox/xxxxxxxx.default where xxxxxxx is a string of random letters and numbers, then restart firefox.

If that doesn't work open a terminal and type:

```
firefox
```

and see  what errors you get.

Jim

---

