---
title: "Help me put the AMP back in LAMP"
date: 2008-05-15
forum: Server Platforms
---

### Post by rikoshay on 2008-05-15
Hi,

I've just rolled out an 8.04 server at a remote location that I connect to via SSH. When originally installing it I selected the LAMP and SSH packages. To cut a long story short I've basically screwed up the Apache2MySQLPHP component by trying to invent my own shortcuts when trying to migrate a few websites and their virtual hosts. I am a moron. ](*,)

I've spent the evening uninstalling and reinstalling various components but none of them want to play nicely with each other anymore. As I see it I have two options:

1. Reinstall the server from scratch
2. Cleanly uninstall and reinstall Apache2 MySQL and PHP

I really don't want to do option 1 as the server is a couple of hundred miles away but I don't know how to do option 2. Any help much appreciated.

---

### Post by doogy2004 on 2008-05-15
try removing the selections from the following command

```
sudo tasksel
```

let it run to completion then run it again and add the stuff you want back in

---

### Post by rikoshay on 2008-05-16
Many thanks. That sort of worked but left a lot of the bad configuration files. I eventually fixed the problem with

```
sudo aptitude purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql

sudo rm -rf /etc/apache2

sudo aptitude install apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
```

Everything now seems to be working.

---

