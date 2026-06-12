---
title: "AMP+Python on Desktop Hardy"
date: 2008-04-30
forum: Server Platforms
---

### Post by Pericius on 2008-04-30
How to install Apache/MySql/PHP/Python server on Ubuntu 8.04? I guess it's a apt-get one-liner, but I don't know what to do make Python work. I need it only for site development.

And, if it's not too much of a problem, could someone hint at configuration steps afterwards?

Thanks in advance.

---

### Post by bluefrog on 2008-04-30
for LAMP, you could use sudo tasksel.
for python, I assume sudo apt-get install python will do

---

### Post by cdenley on 2008-04-30
> **bluefrog said:**
> for LAMP, you could use sudo tasksel.
for python, I assume sudo apt-get install python will do

Unless you want python web scripts to run in apache.
```

sudo apt-get install libapache2-mod-python
sudo /etc/init.d/apache2 restart

```

---

### Post by ibutho on 2008-04-30
The command below is a good starting point
```
sudo aptitude install apache2 mysql php5-mysql libapache2-mod-python
```
Python is installed by default on most Linux distros, so all you need is the apache module.

---

### Post by Pericius on 2008-05-02
> **ibutho said:**
> The command below is a good starting point
```
sudo aptitude install apache2 mysql php5-mysql libapache2-mod-python
```
Python is installed by default on most Linux distros, so all you need is the apache module.
It oughta be mysql-server package but otherwise it worked great. Thanks a bunch!

---

