---
title: "Remote Access to mysql server on ubuntu"
date: 2008-11-29
forum: Server Platforms
---

### Post by abhinav90 on 2008-11-29
Hi i have just installed apache2, mysql and phpmyadmin on my server, What i wanted to know was how to find the external host name of the mysql server as i have a java widget program that needs to remotely query the database. i have done this on a shared managed host cause they gave me the external mysql host name.

How do i find my mysql's host name. I have a static ip access for my server already enabled. 

I think there is some way of using mysqlaccess -rhost or -H to do so but i dont know how.

Any help would be appreciated!

---

### Post by abhinav90 on 2008-11-29
Hi i have just installed apache2, mysql and phpmyadmin on my server, What i wanted to know was how to find the external host name of the mysql server as i have a java widget program that needs to remotely query the database. i have done this on a shared managed host cause they gave me the external mysql host name.

How do i find my mysql's host name. I have a static ip access for my server already enabled. 

I think there is some way of using mysqlaccess -rhost or -H to do so but i dont know how.

Any help would be appreciated!

---

### Post by cariboo on 2008-11-29
The mysqls host name is the name of your computer, you should have named you server while setting it up to check what the host name is at the prompt type:

```
hostname -a
```

The -a is just in case you gave your server an alias.

To access mysql remotely, at the prompt type:

```
mysql -h <hostname> -u <user name> -p
```

Jim

---

### Post by Philio on 2008-11-29
Your MySQL hostname should be accessable via the same hostname or IP address of your server.

BUT, you need to make sure of a couple of things:

1. If you have a firewall in place (which I hope you do) you will need to open port 3306 to allow remote access to MySQL. I would highly recommend that you open it to IP addresses you need to connect to it from ONLY and do not allow full public access to your MySQL server.

2. You might need to check that MySQL is configured to listen for TCP connections and not just local connections via unix socket. It should be enabled by default.

3. You'll obviously need to create a user/database for your remote widget. I would strongly suggest you create a user account that is only available from your IP/hostname and ensure it has nothing other than basic access (SELECT, INSERT, UPDATE, DELETE at most).

Hope this helps :)

---

