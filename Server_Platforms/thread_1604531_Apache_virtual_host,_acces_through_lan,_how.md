---
title: "Apache virtual host, acces through lan, how?"
date: 2010-10-24
forum: Server Platforms
---

### Post by Ordes on 2010-10-24
trying to setup apache, php server.

i got eveything running so far. my problem is with virtualhost so i can have multiple web-roots. this server is for home & design use only, so i dont allow access from the internet. and need my individual web-folders be assigned as "root"-folder.

so far, my virtualhost are working and i can access it from the server machine by e.g "web-site1" (which is bind in /etc/hosts to 127.0.0.1)

my question: how shall i proceed when i want to be able to access this site from my main pc over lan 192.168.x.x ?

i can access the server by 192.168.x.x .. but it will always end in the /var/www.. 

i would like to be able to enter e.g. web1, web2, through my lan...  
so that /var/www/web1 , /var/www/web2 will be "root"-web-folder 

i googled a lot. but everything i found ha sth to do with dyndns, but i just want lan access.

txs

---

### Post by Ordes on 2010-10-24
ok.. i figured it out..

i set my port.conf to

virtual: 192.168.x.x
Listen: 81
Listen: 82

than in the sites-available using for virtual server the 192.168.x.x:81 etc

everything is working so far... but another problem arised...

after setting my ports.config i cannot access phpmyadmin anymore.. local or from the machine..

i changed the mysql/my.conf 
bind: 192.168.....

trying to connect by 192.168...:3306
or just by 192.168.... but always unable to connect.. where else do i have to set the ip for phpmyadmin ? or ports ?

txs

---

### Post by pipuntu on 2011-03-25
Hi,

Realise this post a little old, did you find a solution? Looking for this set up also.

---

