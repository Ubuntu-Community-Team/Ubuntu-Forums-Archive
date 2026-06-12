---
title: "unable to acces my web project"
date: 2013-01-04
forum: Server Platforms
---

### Post by swaggerlee on 2013-01-04
HI all i recently join the community n i got a question 

> i installed ubuntu 12.04 and config apache php mysql.  i developed a web project which i kept in /var/www/(my project)
note- my ip address 192.168.xx.xxx  now my co worker are unable to view the web application via browser

i.e. when the type in there browser  [my.ip.add.ress/my_project] 
they r unable to see  it says  "connecting ..."  n still browseing
what cud be the possible error  plz help me m newbei in linux enviroment 

plzz give me step by step troubleshoot

i really need it badly my co-workers are waiting ......:/

in addition
> when i open my project in my own browser i use
 [http://localhost/my_project](http://localhost/my_project)   it works fine  but on the same when i use [http://my.ip.add.ress/my_project](http://my.ip.add.ress/my_project)  its still connecting n browsing...n so on

---

### Post by volkswagner on 2013-01-04
Do you have the index.html file still located in /var/www?
Can the remote machines access the server by it's ip without adding /my_project.

Possibly the web app has strict "listen" directive on what url it will respond to.

Take a look at Apache2 logs for more info.

---

