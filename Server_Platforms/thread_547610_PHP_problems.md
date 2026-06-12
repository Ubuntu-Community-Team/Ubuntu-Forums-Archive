---
title: "PHP problems"
date: 2007-09-10
forum: Server Platforms
---

### Post by Nirva on 2007-09-10
Hay,

I am trying to setup a simple apache and php server.  
I installed all packets through apt-get but I still have some problems.

1 ) I can not connect to my apache server by going to [http://localhost/](http://localhost/)
 or [http://127.0.0.1](http://127.0.0.1).  I can only connect to it  by going to [http://192.168.1.3](http://192.168.1.3) ( this is my IP-adress on our network at home )

2 ) I can put .html files in /var/www and they work as they should, but when I try executing a .php file, I get this error : 

Not Found
The requested URL /php5-cgi/test.php was not found on this server.

I think these are stupid errors, but I don't know much about servers.

Thanks in advance

---

### Post by NewbieNik on 2007-09-10
Sounds like 2 seperate errors.

Localhost....Check your /etc/hosts file to check that 127.0.0.1 is set for localhost and not 127.0.1.1 as I have seen before.

PHP....make sure your php files are under the /var/www folder or sub-folders and try to access them through firefox. If it doesn´t work then check the php applications lines are uncommented in the apache2.conf in /etc/apache2. This is covered in multiple apache and php docs and in all the documentation.
Can´t provide links at the moment, sorry.
Will try later if you haven´t resolved it.

---

### Post by Nirva on 2007-09-10
Thanks, one of the two problems is solved. 
I can acces my server through [http://localhost](http://localhost)

But the other one isn't solved, cause I am sure that the .php files are located in /var/www
And these are the last lines of my /etc/apache2/apache2.conf

LoadModule actions_module /usr/lib/apache2/modules/mod_actions.so

ScriptAlias /php5-cgi /usr/lib/cgi-bin/php5

AddHandler php5 .php
Action php5 /php5-cgi

Does anyone has a solution?

Thanks

---

### Post by Nirva on 2007-09-10
Installing php5-cgi solved the other problem thanks

---

