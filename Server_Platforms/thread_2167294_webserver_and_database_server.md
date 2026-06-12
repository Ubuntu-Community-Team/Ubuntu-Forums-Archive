---
title: "webserver and database server"
date: 2013-08-13
forum: Server Platforms
---

### Post by my4 on 2013-08-13
Hi, Im new to ubuntu..I have just a little bit problem in connecting to my database server.

I have  installed 2 server running in virtual machine for test purposes

server1 and server2 in server1 I installed apache2 libapache2-mod-php5 php5  php5-mysql phpmyadmin and in server2 I installed mysql-server-5.5.the web server is running fine but I cant connect to my database server...

Please give me idea what to change or what file I need to configure for me to able to connect to my database server.

Thanks a lot guys..

---

### Post by Cheesemill on 2013-08-13
Are both VM's on the same network?

Have you edited the MySQL configuration to allow for network access?  (Comment out the bind-address directive in /etc/mysql/my.conf)

Does the MySQL user you are trying to connect with have the correct permissions?

---

### Post by my4 on 2013-08-13
Thanks for the reply

Yes it is both in virtual and the same network

I have not editted any configuration since I dont knew what configuration I will edit

---

### Post by my4 on 2013-08-13
> **Cheesemill said:**
> Are both VM's on the same network?

Have you edited the MySQL configuration to allow for network access?  (Comment out the bind-address directive in /etc/mysql/my.conf)

Does the MySQL user you are trying to connect with have the correct permissions? bind address by default is uncomment. by the way how to set correct permission?

---

### Post by Cheesemill on 2013-08-13
> **my4 said:**
> bind address by default is uncomment
I know, that's why I told you to turn it into a comment

> by the way how to set correct permission?
When you create your MySQL users they need to be allowed network access, not just localhost access. For example...
```
CREATE USER 'jeffrey'@'192.168.0.0/24' IDENTIFIED BY 'mypass';
```

not...
```
CREATE USER 'jeffrey'@'localhost' IDENTIFIED BY 'mypass';
```

---

### Post by my4 on 2013-08-13
> **Cheesemill said:**
> I know, that's why I told you to turn it into a comment


When you create your MySQL users they need to be allowed network access, not just localhost access. For example...
```
CREATE USER 'jeffrey'@'192.168.0.0/24' IDENTIFIED BY 'mypass';
```

not...
```
CREATE USER 'jeffrey'@'localhost' IDENTIFIED BY 'mypass';
``` i have commented the bind address....I'm sorry I'm a lil beat slow,when I installed mysql-server5.5 it automatically create a user which is root by default and a user defined password..those code above Is for server1 or server2?

---

### Post by Cheesemill on 2013-08-13
That's just an example.

When you create your MySQL user(s) needed for whatever web application you are trying to install you need to make sure you give the user access to MySQL over the network.

Tell us what you are installing that needs MySQL and I can probably give you better information.

---

### Post by my4 on 2013-08-13
> **Cheesemill said:**
> That's just an example.

When you create your MySQL user(s) needed for whatever web application you are trying to install you need to make sure you give the user access to MySQL over the network.

Tell us what you are installing that needs MySQL and I can probably give you better information.

Here it all goes..I have try manual installation of LAMP server in a single machine only it is running well there's no problem...to expand my knowledge now I want to try to install 2 machine which is the database server is in the other machine.My problem is how to do this tricks..

---

### Post by nerdtron on 2013-08-13
Just a reminder, if you configured the firewall, it might be blocking some ports. :)

---

### Post by my4 on 2013-08-13
> **nerdtron said:**
> Just a reminder, if you configured the firewall, it might be blocking some ports. :) there's no firewall set

---

### Post by Cheesemill on 2013-08-13
What errors are you getting?

If you have commented out the bind-address line and restarted MySQL then it should now be listening on its network interface.

Can you run the following from your web server and let us know what happens...
```
mysql -u <username> -p -h <mysql_IP_address>
```

---

### Post by SeijiSensei on 2013-08-13
> **Cheesemill said:**
> When you create your MySQL users they need to be allowed network access, not just localhost access. For example...
```
CREATE USER 'jeffrey'@'192.168.0.0/24' IDENTIFIED BY 'mypass';
```

You can grant a user access on all interfaces with
```
CREATE USER 'jeffrey'@'%' IDENTIFIED BY 'mypass';
```

which uses the standard SQL wildcard character to represent the hostname.

---

