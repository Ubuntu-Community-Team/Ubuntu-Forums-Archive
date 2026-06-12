---
title: "Mysql help"
date: 2007-11-08
forum: Server Platforms
---

### Post by white_shadow on 2007-11-08
Hi. i have installed mysql, but i can't acess to mysql from the others computer to the server, i get this message:

shel: mysql -uroot -pPassword -h192.168.2.104 
result:
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.2.104' (10061)

I also can't access with other usres created, like marco, mbranco, or others.

What i have else to do?

Thank's

---

### Post by reckless2k2 on 2007-11-08
in my.conf it's setup only to accept from localhost as a security measure. you have to change the address for your network.

i just install phpmyadmin and then tweak the conf to allow from my network to login. same thing.

---

### Post by white_shadow on 2007-11-08
How could i do tha?

---

### Post by reckless2k2 on 2007-11-08
which one? the my.conf edit or the phpmyadmin install? hahahaha

[http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

down at the bottom it talks about localhost and the my.conf stuff. 

i think you have to either type 

192.168.0.

or 

192.168.0.1/24

You know about tcp/ip?

like if your network is 192.168.1.1

192.168.3.1..yadda

EDIT: oh you're 2....ok 192.168.2.0/24

---

### Post by reckless2k2 on 2007-11-08
sorry i was wrong. 

use this:

[http://www.trustix.org/wiki/index.php/MySQL_network_access](http://www.trustix.org/wiki/index.php/MySQL_network_access)

i just do it all through the phpmyadmin GUI. it's easier. hahaha

that link is re-enforced here as well..

[http://www.bugzilla.org/docs/2.18/html/security-mysql.html](http://www.bugzilla.org/docs/2.18/html/security-mysql.html)

EDIT: i think i was right. ima goof.

---

