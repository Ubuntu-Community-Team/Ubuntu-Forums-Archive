---
title: "Apache2 - - setting up index.html (not found)"
date: 2011-05-18
forum: Server Platforms
---

### Post by koshiuk on 2011-05-18
Hi, this is probably a simple question, im playing about with 11.04 and from windowz background and having a play with apache2, i've used this guide  [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

the query is, my system doesnt have /home/user directory, the only dir there is my username, /home/dave for example. So i changed the command to /home/dave/public_html/index.html, restart apache2
i run  [http://localhost/](http://localhost/) and get this error below, so i created /home/user/public-html dir,  but it wont create the index.html, permissions denied.....


**Not Found ****The requested URL / was not found on this server.**
**Apache/2.2.17 (Ubuntu) Server at localhost Port 80**

Many thanks......

---------------


Finally, we restart Apache2: 

sudo /etc/init.d/apache2 restart*If you have not created /home/user/public_html/, you will receive an warning message* 
To test the new site, create a file in /home/user/public_html/: 

echo '<b>Hello! It is working!</b>' > /home/user/public_html/index.htmlFinally, browse to [http://localhost/](http://localhost/)

---

### Post by koshiuk on 2011-05-18
Just tried it again and now getting the below so looking good, i think?!?!?

**Index of /**

 [IMG]http://localhost/icons/blank.gif[/IMG][Name]("http://localhost/?C=N;O=D")[Last modified]("http://localhost/?C=M;O=A")[Size]("http://localhost/?C=S;O=A")[Description]("http://localhost/?C=D;O=A")   Apache/2.2.17 (Ubuntu) Server at localhost Port 80

---

