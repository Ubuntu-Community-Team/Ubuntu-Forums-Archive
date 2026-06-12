---
title: "Kolab HOWTO?"
date: 2006-07-31
forum: Server Platforms
---

### Post by LordMerlin on 2006-07-31
Does anyone have a HOWTO for the Kolab project?

---

### Post by adamkane on 2006-07-31
[http://wiki.kolab.org/index.php/Ubuntu](http://wiki.kolab.org/index.php/Ubuntu)

---

### Post by rdjurovich on 2006-09-03
Has anyone had problems installing on 6.06?

After following the Kolab wiki:
```

# apt-get install gcc-3.3 g++-3.3 bison flex make shtool
# cd /usr/bin
# ln -s gcc-3.3 gcc
# ln -s g++-3.3 g++

```
I am able to correctly run the obmtool, however it ends up only installing one or two packages, and therefore does not allow me to bootstrap.

I am looking for a solution, and will post here if I have any updates.
However, in the mean time, if anyone could help me out, it would be appreciated.:D

UPDATE:

Ok, I have figured things out. For some reason, if I installed the g++, this would install gcc and g++ versions 4.0 which would let me run things. I also used 3.4 instead of 3.3 simply because I thought it would be better (don't know if it makes a difference really).
I have updated the Ubuntu howto pages in the official Kolab wiki, so if you are struggling as well, check it out:
[http://wiki.kolab.org/index.php/Ubuntu](http://wiki.kolab.org/index.php/Ubuntu)
:grin:

---

### Post by DigitalDuality on 2006-11-16
does anyone know how to get this working alongside of apache2?

my webserver is also the machine i would be running kolab off of, unfortunately... i can't get the kolab web interface to come up.. at all, even with apache2 turned off, but then i can't access my hosted sites either.

---

### Post by adamkane on 2006-11-17
I don't have time today to test Kolab, but you may need the following to get it working.

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by hyrcan on 2006-12-05
Anyone have docs on the configuration of Kolab via installing through apt-get on edgy?  It looks as if the packages get the files in the right place but none of the settings.  I suspect I just need to go through each peice of the pie and get the settings right, but I've not found any docs on that, only docs for installing from the openpkg.

If you spot something that may help posting here will be a huge help... till then... ](*,)  untill I get it figured out.

---

