---
title: "How to Install ZoneMinder-1.36.0-focal1. on UBUNTU 20.04 LTS ( Focal Fossa)"
date: 2021-05-16
forum: Tutorials
---

### Post by bkjaya1952 on 2021-05-16
```
sudo su

sudo add-apt-repository ppa:iconnor/zoneminder-1.36

sudo apt-get update

apt install zoneminder
```


**Configuring Mysql**


```
/etc/init.d/mysql start

mysql -e "drop database zm;"

mysql -uroot --password=""< /usr/share/zoneminder/db/zm_create.sql 2>/dev/null

mysql -e "ALTER USER 'zmuser'@localhost IDENTIFIED BY 'zmpass';"

mysql -e "GRANT ALL PRIVILEGES ON zm.* TO 'zmuser'@'localhost' WITH GRANT OPTION;"

mysql -e "FLUSH PRIVILEGES ;
```

[B]Configuring Zoneminder
[/B]

```
chmod 740 /etc/zm/zm.conf

chown root:www-data /etc/zm/zm.conf 

adduser www-data video

a2enmod cgi 

a2enconf zoneminder

a2enmod rewrite 

a2enmod headers 

a2enmod expires
```

[B]Starting Zoneminder and apache
[/B]

```
systemctl enable zoneminder

service zoneminder start

service apache2 reload
```


Open zoneminder web console ([http://localhost/zm/](http://localhost/zm/))

---

