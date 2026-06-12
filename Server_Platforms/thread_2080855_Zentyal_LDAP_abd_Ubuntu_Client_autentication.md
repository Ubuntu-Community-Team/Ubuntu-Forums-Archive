---
title: "Zentyal LDAP abd Ubuntu Client autentication"
date: 2012-11-05
forum: Server Platforms
---

### Post by miguelpires on 2012-11-05
Hello,
I really need help from someone:
I have this for the LDAP server:

DN base: dc=ponteconta-domain,dc=lan
Raiz DN: cn=zentyal,dc=ponteconta-domain,dc=lan
Password: 2Cm2n43btL31fQn8eWQq
Utilizadores DN: ou=Users,dc=ponteconta-domain,dc=lan
Grupos DN: ou=Groups,dc=ponteconta-domain,dc=lan

I configured the LDPA client runing Ubuntu with this 

[http://askubuntu.com/questions/127389/how-to-configure-ubuntu-as-an-ldap-client](http://askubuntu.com/questions/127389/how-to-configure-ubuntu-as-an-ldap-client)

But i can't connect the client to the server. Any help for debugging?
Regard's
Miguel

---

### Post by miguelpires on 2012-11-11
bump

---

### Post by foxuser on 2012-11-11
Hi,

I think LDAP in Zentyal is using port 390 and you have to open in Zentyal firewall.

You can find more information at:

[http://doc.zentyal.org/](http://doc.zentyal.org/)

[http://forum.zentyal.org/](http://forum.zentyal.org/)

---

### Post by miguelpires on 2012-11-11
> **foxuser said:**
> Hi,

I think LDAP in Zentyal is using port 390 and you have to open in Zentyal firewall.

You can find more information at:

[http://doc.zentyal.org/](http://doc.zentyal.org/)

[http://forum.zentyal.org/](http://forum.zentyal.org/)

Hi,
Yes I've done that, be default its denied. 

My problem is i Can't authenticated. I really don't know what I'm doing wrong. 
Really appreciate the help.

Regard's
Miguel Pires

---

### Post by foxuser on 2012-11-11
I use Zentyal but without ldap autentication.

Found the tread at Zentyal Foruns

[http://forum.zentyal.org/index.php/topic,11923.0.html](http://forum.zentyal.org/index.php/topic,11923.0.html)

You can try to see if it works

---

### Post by miguelpires on 2012-11-11
> **foxuser said:**
> I use Zentyal but without ldap autentication.

Found the tread at Zentyal Foruns

[http://forum.zentyal.org/index.php/topic,11923.0.html](http://forum.zentyal.org/index.php/topic,11923.0.html)

You can try to see if it works

I wil try. 
I Know that Zentyal have 2 Ldap Servers. Samba use port 389 and the other Ldap use port 390. 
From what i understand they whant to only autenticate 1 time via port 390. 
Tk's for the link

---

