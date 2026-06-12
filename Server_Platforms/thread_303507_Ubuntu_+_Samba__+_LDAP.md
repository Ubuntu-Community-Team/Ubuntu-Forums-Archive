---
title: "Ubuntu + Samba  + LDAP"
date: 2006-11-20
forum: Server Platforms
---

### Post by cyris| on 2006-11-20
Hey everyone.

I am currently following this guide on howto setup an LDAP server and samba but im kinda confused

[http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap)

Does it go through setting up a Samba PDC ?

---

### Post by Macchi on 2006-11-20
> **cyris| said:**
> Hey everyone.

I am currently following this guide on howto setup an LDAP server and samba but im kinda confused

[http://times.usefulinc.com/2005/09/25-ldap](http://times.usefulinc.com/2005/09/25-ldap)

Does it go through setting up a Samba PDC ?
Hello Cyris,

The guide that you've mentioned tells how to authenticate samba users (or machines) through a LDAP server. To setup a Primary Domain Controller it would be neccessary to perform further configuration of the Samba server and clients. It is not impossible but normally takes quite some time. There are other sources like books, articles, guides and tutorials that will explain this configuration process in detail. 

One of my favorite books that cover this is the excellent "Linux Cookbook" by Carla Schroder, published by O'Reilly. Get the book and you will have fast track for a working network with Linux and Windows clients. The book "Windows in a Linux World" by Roderick W. Smith, published by O'Reilly is also very good. These books offer a high value in knowledge at a quite low acquisition price. Most probably they will save you many dozens of workhours and hopeless moments trying to test new samba configuration alternatives. Besides helping you to get a much safer and reliable system.     

(I have to mention this, but I find your avatar less suitable for this type of collaborative forum, because it simply seems to be insulting. Still I try to be constructive and will attemp to help you on your technical issues).

---

### Post by cyris| on 2006-11-20
Thanks for your reply, I will look into getting those books :D

---

