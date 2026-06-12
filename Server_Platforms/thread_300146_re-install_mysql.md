---
title: "re-install mysql"
date: 2006-11-15
forum: Server Platforms
---

### Post by abulliard on 2006-11-15
Hi,
I installed a Ubuntu LAMP 6.06 server. I did some configuration on mysql-server, and I wanted to completely clean-up mysql on my server. I did:
#apt-get remove mysql-server
#apt-get install mysql-server
But my configuration and even my data was the same.
So I did:
#rm /etc/mysql/*

The problem is now I don't know how to recreate /etc/mysql/debian.cnf and debian-start.

Could someone help me?
- how can I get back a working system?
- in the future, how can I clean up my mysql installation if a want to start again from scratch?

Thank you very much!

Aymeric

---

### Post by tturrisi on 2006-11-15
to cleanup leftover files do:
apt-get --purge remove mysql-server
reinstall:
apt-get install mysql-server
By default, mysqlserver won't remove the databases on uninstall.
easily manage the databases:
apt-get install phpmyadmin
access phpmyadmin:
[http://local-ip-address/phpmyadmin](http://local-ip-address/phpmyadmin)
login:
username: root
password: don't type a password
once inside:
go to Privledges and set passwords

---

### Post by richb01 on 2006-11-19
Hi, All,

I think I'm in a similar situation (a corrupted install of mysql).  I would like to *completely* uninstall everything: all database files, all scripts, configs, everything and start totally fresh.

Can some kind person tell my how to do that?  I'm fairly new with Ubuntu (I've had it installed about a week).

TIA!  :-)
Rich

---

### Post by aash on 2006-12-05
> **abulliard said:**
> Hi,
I installed a Ubuntu LAMP 6.06 server. I did some configuration on mysql-server, and I wanted to completely clean-up mysql on my server. I did:
#apt-get remove mysql-server
#apt-get install mysql-server
But my configuration and even my data was the same.
So I did:
#rm /etc/mysql/*

The problem is now I don't know how to recreate /etc/mysql/debian.cnf and debian-start.

Could someone help me?
- how can I get back a working system?
- in the future, how can I clean up my mysql installation if a want to start again from scratch?

Thank you very much!

Aymeric

Hi 

Try this

try sudo dpkg --purge packagename

This gives removes all mysql traces from you installation, you can then run a new mysql install.

cheers

---

