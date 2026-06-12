---
title: "virtual hosting"
date: 2008-07-09
forum: Server Platforms
---

### Post by kustomjs on 2008-07-09
Hi Guys
I want to know how to get virtual hosting working for 2 different names? because I was looking at this topic before [http://ubuntuforums.org/showthread.php?t=201460&page=1](http://ubuntuforums.org/showthread.php?t=201460&page=1) and I copied the code information and it didnt work so how do I get this to work and here is the 2 different domains I am working with jbodyconnection.com and cbcperformance.net and its on the same server and the server name is server1.

---

### Post by Titan8990 on 2008-07-09
Try this (the first google result of "Ubuntu apache virtual host tutorial"): [http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/](http://www.tequilafish.com/2007/08/02/apache-virtualhost-on-ubuntu/)

Also, it is customary to not include your actual domain name, IP address, or email address in a public forum.

For example, jbodyconnection.com and cbcperformance.net could have easily have been typed as foo.bar and example.com.

---

### Post by kustomjs on 2008-07-09
when I do Enable your new virtualhost:
sudo a2ensite jbodyconnection.com.conf  I get this site does not exist.

---

### Post by Titan8990 on 2008-07-09
Just make a symbolic link from the virtual host file found in /etc/apache2/sites-available to /etc/apache2/sites-enabled. Then restart apache as it says.

---

### Post by kustomjs on 2008-07-09
I get this error apache2: Syntax error on line 299 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/cbcperformance.net: No such file or directory

how do I fix this?

---

### Post by cariboo on 2008-07-09
Symlink:

```
man symlink
```

```
sudo ln -s /somedir/somefile somefile
```

```
man ln
```

Jim

---

### Post by kustomjs on 2008-07-09
VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results.

---

