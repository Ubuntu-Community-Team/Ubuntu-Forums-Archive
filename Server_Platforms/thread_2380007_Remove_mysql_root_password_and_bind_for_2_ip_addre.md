---
title: "Remove mysql root password and bind for 2 ip addresses"
date: 2017-12-12
forum: Server Platforms
---

### Post by dam034 on 2017-12-12
Dear users,

the title of this thread says everything.

I want to remove the mysql root password via terminal, I executed this command:
```
mysql> update user set password=PASSWORD('') where User='root';
ERROR 1054 (42S22): Unknown column 'password' in 'field list'
```
But as you can see I receive an error.

And after I want to bind the mysql service for localhost and another LAN ip. Now bind_address is 127.0.0.1


How can I fix?

EDIT:
I managed to remove the root password with this command:
```
mysql> SET PASSWORD FOR 'root'@'localhost' = '';
```

And for binding the server, I commented the bind-address parameter, and I added some firewall rules to accept connections from only one external ip on port 3306.



Thanks

---

