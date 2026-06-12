---
title: "MySql frontend"
date: 2010-09-04
forum: Server Platforms
---

### Post by Ghost_Mazal on 2010-09-04
Lo Guys ,

What is a good MySql frontend to manage your MySql databases from another pc ?
I used to use Jheidi and use HeiSql in Windows. But Jheidi for linux has been discontinued and doesn't seem to be compatible with the latest Ubuntu.

What can you guys recommend ? It must be able to create MySql users , create and manage databases as well as all data functions in the databases.

Thanx

---

### Post by BkkBonanza on 2010-09-04
If you have a web server on the system then the easiest, most flexible option is probably phpMyAdmin. It can do everything you need.

---

### Post by Ghost_Mazal on 2010-09-04
Isn't that tricky to compile and install ?

---

### Post by BkkBonanza on 2010-09-04
Nope. It is a package in the Ubuntu repos "phpmyadmin". I didn't install mine that way because I had it from years ago and just copied it from my old server. It doesn't need to be compiled anyway. Since it's PHP code it would need PHP installed on your server, but that is also a package.

If you do end up using it across the web I'd set it up using "https" so that any database stuff is encrypted across the web. This is a bit more work from the web server side, if you don't have other ssl sites already.

There are other options I tried from time to time but I found this the most convenient and useful. I've used it for years to tweak and manage online data for my server.

---

### Post by adrianx on 2010-09-04
Have you tried MySQL Administrator and MySQL Query Browser?

---

### Post by Ghost_Mazal on 2010-09-04
> **BkkBonaza said:**
> Nope. It is a package in the Ubuntu repos "phpmyadmin". I didn't install mine that way because I had it from years ago and just copied it from my old server. It doesn't need to be compiled anyway. Since it's PHP code it would need PHP installed on your server, but that is also a package.

If you do end up using it across the web I'd set it up using "https" so that any database stuff is encrypted across the web. This is a bit more work from the web server side, if you don't have other ssl sites already.

There are other options I tried from time to time but I found this the most convenient and useful. I've used it for years to tweak and manage online data for my server.

Thanx will check it out. It's on my lan so won't need ssl

> **adrianx said:**
> Have you tried MySQL Administrator and MySQL Query Browser?

Nope , don't know any of those. Will check it out thanx.

---

### Post by spynappels on 2010-09-04
The MySQL Dashboard incorporates tools for administrating and querying databases and managing the servers they run on and is available in the Repos. It is released by the developers of MySQL.

---

### Post by Ghost_Mazal on 2010-09-04
Can't find any MySql Dashboard tool on their site , just a MySql workbench that doesn't have a web interface. The same for Mysql administrator , doesn't exist anymore

---

### Post by FuturePilot on 2010-09-04
Have you tried mysql-admin? It's in the repos.

```
sudo apt-get install mysql-admin
```

---

### Post by adrianx on 2010-09-04
> **Ghost_Mazal said:**
> Can't find any MySql Dashboard tool on their site , just a MySql workbench that doesn't have a web interface
I'm not sure about Dashboard (but it is probably what you need), but MySQL Administrator and Query Browser are in the repos. In other words, search for them using "Software Manager" or whatever it is called. (Sorry, I'm not in Ubuntu right now). No need to go to the MySQL site.

These client applications don't have web interfaces, but they can be used to administer/query remote machines.

---

### Post by Ghost_Mazal on 2010-09-04
I'm gonna give the MySql Workbench a go. Think it will do what I want. Will just have to admin from 1 pc then. If that doesn't do the trick I will go to the repo's for those others

---

