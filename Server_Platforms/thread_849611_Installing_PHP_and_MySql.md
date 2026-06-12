---
title: "Installing PHP and MySql"
date: 2008-07-04
forum: Server Platforms
---

### Post by danielgroves on 2008-07-04
Hi,

I am not planning to run my Linux machine as a server.  I am a Web Designer, but I am fairly new to Linux.  I need to install both PHP and MySql in my computer so that I can run applications like wordpress that are normally run on server to complete testing on them.  

Can anybody help me with this as I have no idea where to even begin!

Thanks!

Dan

---

### Post by RealPSL on 2008-07-04
The easiest way to begin is probably installing the lamp-sever task from the command line. This will install all the components you need. The command to install it is ```
sudo tasksel install lamp-server
```

Once you have it installed you can follow the introductory instructions at this link to get started.

[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html]("http://doc.ubuntu.com/ubuntu/serverguide/C/index.html")

Focus on sections 9 and 10. There are ways to run the installation from synaptic (GUI package manager) but I am not 100% sure what they are but I am sure others will comment.

---

### Post by danielgroves on 2008-07-05
This didn't work. I didn't get any error messages or anything :-k, the PHP files just would not open in Firefox!

Any other ideas?

---

### Post by RealPSL on 2008-07-05
Daniel, what happened when you ran the test listed in at the end of the document that I linked to? Did it ask you to download the php file instead of processing it? Can you provide the httpd logs in /var/log/httpd? That might give some indication on why your php files are not being processed.

---

### Post by danielgroves on 2008-07-06
Yes. The browser did ask me to download the file instead of processing it.  The log in "/var/log/httpd" does not appear to exist, although there are some MySql logs, and now an Apache 2 folder.  Below is the copy of the Apache 2 'error.log' id it is any use:


[Sat Jul 05 13:43:22 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Jul 05 14:30:19 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Jul 05 14:30:31 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Jul 05 14:30:32 2008] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Sat Jul 05 14:30:32 2008] [notice] Apache/2.2.8 (Ubuntu) configured -- resuming normal operations
[Sat Jul 05 14:55:32 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sat Jul 05 14:55:42 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch configured -- resuming normal operations
[Sat Jul 05 15:01:51 2008] [error] [client 127.0.1.1] script '/var/www/phpinfo.php' not found or unable to stat
[Sat Jul 05 15:01:51 2008] [error] [client 127.0.1.1] File does not exist: /var/www/favicon.ico
[Sat Jul 05 15:01:54 2008] [error] [client 127.0.1.1] File does not exist: /var/www/favicon.ico
[Sat Jul 05 15:02:00 2008] [error] [client 127.0.0.1] script '/var/www/phpinfo.php' not found or unable to stat
[Sat Jul 05 15:02:00 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sat Jul 05 15:02:03 2008] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Sat Jul 05 20:47:27 2008] [notice] caught SIGWINCH, shutting down gracefully
[Sun Jul 06 10:40:13 2008] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch configured -- resuming normal operations

---

### Post by danielgroves on 2008-07-06
Sorry for causing trouble, but I have just discovered that I was using the wrong Apache folder as the root, but I am now left with a new dilemma, how do I change the permissions in the correct root folder so root no longer owns it, and so I can add all necessary files, and carry out the check, again?

---

### Post by RealPSL on 2008-07-06
Daniel,

Since you do not own the files you will need to use sudo to change the ownership. For example if the directory with the files is /var/www/html/mysite you would use ```
sudo chown -R username /var/www/html/mysite
```. Be very careful with the -R option as that will change all the files in the directory as well. If that is not what you want simple remove the -R to just change the ownership on that directory.

To check that you have made the changes successfully use ```
ls -lR /var/www/html/mysite
``` again /var/www/html/mysite should be replaced with the locations of your files.

---

### Post by danielgroves on 2008-07-06
I have now got PHP up and running, along with MySql(I Think).  But the problems continue! 

Below is a list of current databases:

```
mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema | 
+--------------------+
1 row in set (0.00 sec)
```

MySql will only let me create a Database called test:

```
mysql> CREATE DATABASE test;
Query OK, 1 row affected (0.00 sec)
```

It will not let me create a Datbase with any other name?!?!?!

```
mysql> CREATE DATABASE main;
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'main'
```


Any ideas how I can fix this? Oh and I think I am logged on ok, but the set-up did not let me create a root password for MySql. I tried uninstalling MySql, and then reinstalling, but this did not work either.

---

### Post by danielgroves on 2008-07-06
All is fine now, I found that root had picked up my normal password!

---

### Post by cariboo on 2008-07-06
The Msql postinst script ask you for a root password, but you should add another user and avoid using root as much as possible. To add another user do the following while running mysql:
```
mysql> grant all privileges on *.* to <user>@localhost
    -> identified by '<password>' with grant option;
Query OK, 0 rows affected (0.00 sec)

mysql> grant all privileges on *.* to <user>@'%'
    -> identified by '<password>' with grant option;
Query OK, 0 rows affected (0.00 sec)

mysql> flush privileges
    -> ;
Query OK, 0 rows affected (0.00 sec)
```

Remember the less you use root the safer.

Jim

---

### Post by danielgroves on 2008-07-07
Thankyou

---

