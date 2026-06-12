---
title: "MySQL user with all permission on all databases from remote host"
date: 2008-04-14
forum: Server Platforms
---

### Post by rslrdx on 2008-04-14
How do i grant a single user, access from another box with full administrative rights.

I have 2 server boxes, one will run apache, the other just DBs,

192.168.2.11 runs apache
192.168.2.12 runs MySQL

I get access denied when i try to access the .12 server from any box.

i created the user "mysqladmin" and gave it full rights using webmin, even changed it alot... nothing works, even tried phpmyadmin with no luck... so I think i better not give much more details hoping to get a clean answer.

I want to use the same administrator user name for several DBs.

Thanks.
Rodrigo.

---

### Post by rslrdx on 2008-04-14
anyone? anything?

i cant be the first one trying to do this.

---

### Post by hyper_ch on 2008-04-15
create a new user through the pma interface, give him access from everywhere and to all databases..

---

### Post by Deathrend on 2008-04-15
My MySQL's a bit rusty, but I think you're looking for

```

grant all privileges on *.* to '<user>'@'%'
identified by '<password>' with grant option

```

Edit: on reread, make sure to take note of the "%", most of the time this is set to "localhost" which will only accept connections to "localhost" meaning the loopback.

---

