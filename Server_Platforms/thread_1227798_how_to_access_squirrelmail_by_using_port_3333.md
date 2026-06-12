---
title: "how to access squirrelmail by using port 3333"
date: 2009-07-31
forum: Server Platforms
---

### Post by pawan_lal on 2009-07-31
hello friends,
i had configured postfix in  **Ubuntu 8.04Lts**  n installed  squirrelmail. i want to access squirrelmail through port 3333. how i installed squirrelmail

apt-get install squirrelmail php-pear
cp /etc/squirrelmail/apache.conf /etc/apache2/conf.d/squirrelmail.conf
/etc/init.d/apache2 restart
/usr/sbin/squirrelmail-configure
command: D
Command >> courier
Command >> S to save
Command >> Q to quit..
[http://192.168.1.141/squirrelmail](http://192.168.1.141/squirrelmail)

n than i changed the port in
/etc/apache2/ports.conf

Listen 3333

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

n than i did port forward 3333 in my router but i am not able to access squirrelmail by doing this, plz guide me in accessing squirrelmail 
thx

---

### Post by dipeshmehta on 2009-08-01
check if your firewall blocks port 3333 ?

---

