---
title: "Postfix+Courier with Squirrelmail"
date: 2010-03-07
forum: Server Platforms
---

### Post by Cpt Crayon on 2010-03-07
Greetings,

I have struck a small problem. In following the guide from 
[http://flurdy.com/docs/postfix/edition7.html#config-simple-imap](http://flurdy.com/docs/postfix/edition7.html#config-simple-imap)

Was able to sucessfully set up the postfix and courier parts of the mail server, being able to send out emails, and reciveve from internal clients Ok. but when it came time to try squirrelmail, I am not having any luck. When browsing to the squirrelmail address i keep getting  "404 Not Found" 

I have looked in all the obvious placed (To me that is!), but to no avail. The frustrating thing is that I also have phpmyadmin running and access to that is fine.

All apps were installed using apt.

Can anyone suggest where to start looking?

running Ubuntu Server 9.04
apache2
courier
postfix
Mysql
clamav

Cheers in advance.

---

### Post by kewlrichie on 2010-03-08
Checkout this guide the link should bring you to the squirrelmail part [http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p5]("http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3-p5")

---

### Post by Cpt Crayon on 2010-03-08
Thanks for the Reply and link. But after some careful searching through the logs discovered that the httpd.conf file in apache was pointing to the wrong directories for the php files..  arrgg

Now works a treat!

Cheers,

FB

---

