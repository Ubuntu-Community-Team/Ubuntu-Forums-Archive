---
title: "How do I install Apache and MySql on Ubuntu Desktop?"
date: 2009-01-19
forum: Server Platforms
---

### Post by futureal2032 on 2009-01-19
Ok,
this may sound stupid..or naive...but

I am using Ubuntu 8.10 Desktop edition..
and i am going to learn PHP..
so i would like to install Apache and My Sql on my Ubuntu Desktop version..

is it possible? or you have to have Ubuntu Server edition?

if possible..where can i get info on doing it?

---

### Post by Coreigh on 2009-01-19
You should be able to find Apache and MySQL in the add remove programs utility on the Applications Menu, or in Synaptic Package Manager in the System Admin Menu, or installing it with apt-get from the command line.
```
sudo apt-get update
```
then
```
sudo apt-get install apache2 mysql-server
```

You might want to add mysql-admin or phpmyadmin for a graphical interface for MySQL.

---

### Post by martien on 2009-01-19
And also you need php... don't you?
```
apt-get install php5 php5-gd php5-mcrypt php5-mysql libapache2-mod-php5
```

---

### Post by Chris of Arabia on 2009-01-19
Or you could use this, which would include the PHP5 install with the deal

```
sudo tasksel install lamp-server
```

---

### Post by Maheriano on 2009-01-19
> **Chris of Arabia said:**
> Or you could use this, which would include the PHP5 install with the deal

```
sudo tasksel install lamp-server
```

WINNER. This is what I did, works perfect. I'll see if I can find the guide I used...

EDIT - here it is - [http://ubuntuforums.org/showpost.php?p=6327257&postcount=6](http://ubuntuforums.org/showpost.php?p=6327257&postcount=6)

---

### Post by Chris of Arabia on 2009-01-20
Glad to be of help, but the credit should go to cb951303 who I picked that one up from earlier in the day.

---

