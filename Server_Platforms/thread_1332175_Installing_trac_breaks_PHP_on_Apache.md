---
title: "Installing trac breaks PHP on Apache"
date: 2009-11-20
forum: Server Platforms
---

### Post by sipickles on 2009-11-20
Hi,

I have a Ubuntu Server 9.04 setup, running LAMP. All was working well until I installed subversion and trac.

Now when a browser requests a php file from apache (eg, index.php) the server serves the php file as a download rather than processing it and serving HTML.

Anyone else had this?

Thanks

---

### Post by dgoosens on 2009-11-20
you might want to check if php is loaded...
check in /etc/apache2/mods-enabled whether php5.conf is present..

if not do
```
sudo a2enmod php5
```

---

### Post by sipickles on 2009-11-20
> **dgoosens said:**
> 
check in /etc/apache2/mods-enabled whether php5.conf is present..


Indeed it isnt! wtf?

I had reinstall with:

```
sudo apt-get install php5 libapache2-mod-php5

sudo /etc/init.d/apache2 restart
```

Not sure where my php went!

---

