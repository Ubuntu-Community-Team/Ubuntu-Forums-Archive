---
title: "Lamp-server problem!!!"
date: 2011-08-19
forum: Server Platforms
---

### Post by IT Support on 2011-08-19
hi guys!! 
i  have installed lamp-server 
everything was installed good but  i have strange problem 


if i creat some php file in /var/www i can see it in browser but if i will copy some scripts there (i mean Data Life Engine 9.2) browsers can`t see installation package, i tryed  diferent packages :(

maybe someone had  problem with lamp-server ??
i need it realy 

please repley :)

[img]http://a.pix.ge/y/er81u.png[/img]

---

### Post by Wim Sturkenboom on 2011-08-19
I would first check the apache error logs in /vat/log/..../error.log (.... is either something with http or something with apache in it). They will tell you exactly what is wrong.

Maybe you can show us the folder structur and the permissions. Install the tree package and run *_tree -p /var/www_*. You only have to show a few files per directory.

Below an example for /var/lib/mysql (as I don't have apache installed)
```

wim@desktop-01:~$ sudo tree -p /var/lib/mysql
/var/lib/mysql
&#9500;&#9472;&#9472; [-rw-r--r--]  debian-5.1.flag
&#9500;&#9472;&#9472; [-rw-rw----]  desktop-01.pid
&#9500;&#9472;&#9472; [-rw-rw----]  ibdata1
&#9500;&#9472;&#9472; [-rw-rw----]  ib_logfile0
&#9500;&#9472;&#9472; [-rw-rw----]  ib_logfile1
&#9500;&#9472;&#9472; [drwx------]  mysql
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  columns_priv.frm
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  columns_priv.MYD
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  columns_priv.MYI
...
...
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition.MYI
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition_type.frm
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition_type.MYD
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition_type.MYI
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  user.frm
&#9474;   &#9500;&#9472;&#9472; [-rw-rw----]  user.MYD
&#9474;   &#9492;&#9472;&#9472; [-rw-rw----]  user.MYI
&#9500;&#9472;&#9472; [-rw-rw----]  mysql_upgrade_info
&#9492;&#9472;&#9472; [drwx------]  mytestdb
    &#9500;&#9472;&#9472; [-rw-rw----]  db.opt
    &#9500;&#9472;&#9472; [-rw-rw----]  sometable.frm
    &#9500;&#9472;&#9472; [-rw-rw----]  sometable.MYD
    &#9492;&#9472;&#9472; [-rw-rw----]  sometable.MYI

2 directories, 79 files
wim@desktop-01:~$

```




> 
maybe someone had problem with lamp-server ??

Not me ;)

---

### Post by IT Support on 2011-08-19
> **Wim Sturkenboom said:**
> I would first check the apache error logs in /vat/log/..../error.log (.... is either something with http or something with apache in it). They will tell you exactly what is wrong.

Maybe you can show us the folder structur and the permissions. Install the tree package and run *_tree -p /var/www_*. You only have to show a few files per directory.

Below an example for /var/lib/mysql (as I don't have apache installed)
```

wim@desktop-01:~$ sudo tree -p /var/lib/mysql
/var/lib/mysql
&#9500;&#9472;&#9472; [-rw-r--r--]  debian-5.1.flag
&#9500;&#9472;&#9472; [-rw-rw----]  desktop-01.pid
&#9500;&#9472;&#9472; [-rw-rw----]  ibdata1
&#9500;&#9472;&#9472; [-rw-rw----]  ib_logfile0
&#9500;&#9472;&#9472; [-rw-rw----]  ib_logfile1
&#9500;&#9472;&#9472; [drwx------]  mysql
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  columns_priv.frm
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  columns_priv.MYD
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  columns_priv.MYI
...
...
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition.MYI
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition_type.frm
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition_type.MYD
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  time_zone_transition_type.MYI
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  user.frm
&#9474;** &#9500;&#9472;&#9472; [-rw-rw----]  user.MYD
&#9474;** &#9492;&#9472;&#9472; [-rw-rw----]  user.MYI
&#9500;&#9472;&#9472; [-rw-rw----]  mysql_upgrade_info
&#9492;&#9472;&#9472; [drwx------]  mytestdb
    &#9500;&#9472;&#9472; [-rw-rw----]  db.opt
    &#9500;&#9472;&#9472; [-rw-rw----]  sometable.frm
    &#9500;&#9472;&#9472; [-rw-rw----]  sometable.MYD
    &#9492;&#9472;&#9472; [-rw-rw----]  sometable.MYI

2 directories, 79 files
wim@desktop-01:~$

```Not me ;)
i had  problem with  old ubuntu  and i though that it was ubuntu problem  i will go from work to  home now  and  check what u write me above and i will reply here  
  

thank you  :)

---

### Post by Wim Sturkenboom on 2011-08-19
I never said that I used Ubuntu servers, and I actually don't use them, so I don't know if it's an Ubuntu problem. Although I'm not very fond of Ubuntu servers (they are too complicated for me ;) ), I doubt it very much.

Tried Ubuntu server once (6.06) and did not know how fast I had to go back to Slackware. Have a test system setup again (this time with 10.04) to try to get my head around doing things the Ubuntu way.

---

### Post by IT Support on 2011-08-19
> **Wim Sturkenboom said:**
> I never said that I used Ubuntu servers, and I actually don't use them, so I don't know if it's an Ubuntu problem. Although I'm not very fond of Ubuntu servers (they are too complicated for me ;) ), I doubt it very much.

Tried Ubuntu server once (6.06) and did not know how fast I had to go back to Slackware. Have a test system setup again (this time with 10.04) to try to get my head around doing things the Ubuntu way.
i found in google  linux debian OS like ubuntu  name is  "edubuntu" it is dvd  disk iso image  and just now i am installing it , i am signed  here with live cd  :) so i will write what will be with new  edubuntu  :) 

by the way anyone know how it`s` work? is it a full  version  and is  there correct bugs ?  :) and why it is so  big in weight? i mean that it is dvd diks image  :)

---

### Post by Wim Sturkenboom on 2011-08-20
It's probably so big because it has a lot of stuff that you, by the way, don't need for a server.

---

### Post by lisati on 2011-08-20
*Thread moved to **Server Platforms**.*

---

