---
title: "apache and &quot;virtual servers&quot;?"
date: 2007-09-09
forum: Server Platforms
---

### Post by rbprogrammer on 2007-09-09
ok, so i am still new to this whole apache configuration files and such, but what i need to do is have a "separate" website on the same server.  my sister wants to build a website, and than when things start to pick up, she will move her stuff to a server that has much more speed then my puny little machine i call a server.

i have webmin installed, i have apache up and running, and i have an account on dyndns.com (the free one).

so what i am thinking is that i add another host on dyndns.com that will forward people to my server.  then i will add a user on the server for my sister so that she can log in with webmin.  the only problem is that i dont know how to do this.

do i need to create a virtual server? so that when people go to her site, apache will go to the right directory and not mine..  also, how do i make it so that she can only edit her files on webmin? i mean like does webmin operate with the permissions of the user she logged in with??

****NOTE**:
these are just my preliminary questions, i'm sure i will have more :) ..

---

### Post by jacksprat99 on 2007-09-09
If you are using apache 2, then a good starting point would be :[http://httpd.apache.org/docs/2.0/vhosts/]("http://httpd.apache.org/docs/2.0/vhosts/")

Sounds like you want a IP based virtual setup since you are using DynDNS..

Be sure to look at the samples on that page entitled "**Virtual Host examples for common setups"**

---

### Post by ruibernardo on 2007-09-09
> **rbprogrammer said:**
> 
i have webmin installed, i have apache up and running, and i have an account on dyndns.com (the free one).

so what i am thinking is that i add another host on dyndns.com that will forward people to my server.  then i will add a user on the server for my sister so that she can log in with webmin.  the only problem is that i dont know how to do this.

do i need to create a virtual server? so that when people go to her site, apache will go to the right directory and not mine..  also, how do i make it so that she can only edit her files on webmin? i mean like does webmin operate with the permissions of the user she logged in with??


Hi rbprogrammer,

to do what you want using webmin is really very easy.

If you still didn't install inadyn, to use with DynDNS, you can see how to install and configure here on [help.ubuntu.com]("https://help.ubuntu.com/community/DynamicDNS"). Then just add another "--alias" line on the file /etc/inadyn.conf for the second site.

To use webmin to add and remove virtual hosts, follow  the instructions on this page on [rimuhosting.com]("http://rimuhosting.com/howto/virtualhosting.jsp"). I think that those instructions in rimuhosting.com explains it very well.

It is very simple, you will see :guitar:

---

### Post by rbprogrammer on 2007-09-10
> **epimeteo said:**
> 
...
If you still didn't install inadyn, to use with DynDNS, you can see how to install and configure here on [help.ubuntu.com]("https://help.ubuntu.com/community/DynamicDNS"). Then just add another "--alias" line on the file /etc/inadyn.conf for the second site.
...


i use ddclient with dynsdns.com, is "inadyn" the same type of program??

---

### Post by ruibernardo on 2007-09-10
Yes it is. But I've never used ddclient, so I can''t tell you how to make you register two (or more) hosts. I know that inadyn does it very well, just by adding another "--alias" line. Check [https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)
 on the section about inadyn.

---

