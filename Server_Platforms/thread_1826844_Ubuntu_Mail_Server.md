---
title: "Ubuntu Mail Server"
date: 2011-08-17
forum: Server Platforms
---

### Post by lavvaf on 2011-08-17
hi
i have a dedicate server that install Ubuntu sever last version and i run joomla with LAMP!
now, i install a Component (RSForm) that i can make form for my site.
i created form and publish it in my site! but when in click submit botton it doesn't send mail to my gmail account!
when i search found i should install mail server in my Ubuntu server but i don't know anything about it! :-\"
I'm beginner on Ubuntu and i need your help to solve my problem. ](*,)
can you help me to explain how dose mail server work?? and what application i should install on my server, too? :(
how can i do it??? 
thankssssssssss very much

---

### Post by ocia on 2011-08-17
I had this problem also on one of my clients' server...
Try installing sendmail ;)
```
apt-get install sendmail
```

If that doesn't fix it, try reading the following page:
[http://josh.st/2005/03/28/ubuntu-sendmail-and-php/]("http://josh.st/2005/03/28/ubuntu-sendmail-and-php/")

Hope this helps!

---

### Post by lavvaf on 2011-08-17
> **ocia said:**
> I had this problem also on one of my clients' server...
Try installing sendmail ;)
```
apt-get install sendmail
```If that doesn't fix it, try reading the following page:
[http://josh.st/2005/03/28/ubuntu-sendmail-and-php/](http://josh.st/2005/03/28/ubuntu-sendmail-and-php/)

Hope this helps!

thank You, I will try it! O:)

---

