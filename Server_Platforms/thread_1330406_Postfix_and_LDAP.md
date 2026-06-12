---
title: "Postfix and LDAP"
date: 2009-11-18
forum: Server Platforms
---

### Post by abishur on 2009-11-18
I'm trying to setup an e-mail server and I want to authenticate to openLDAP (on the same server).  All the help I've been able to find is for a virtual domain and doesn't use the latest releases of postfix (I've installed postfix-ldap and postfix).  I was hoping to get two questions answered:


[LIST=1]
[*]What on earth is a Virtual domain and why is it so Popular?  I'm not working with many users here, do I really want to set up a virtual domain?
[*]Can anyone either: A) tell me the location of a good guide that will teach me how to use postfix and ldap (I will eventually be using dovecot as well) or B) just tell me how to do it in this post?'
[/LIST]
Thanks for any assistance you can provide.  I'm using Ubuntu Desktop 9.10 but thought the server section would be the best place to get help on this issue.

---

### Post by abishur on 2009-11-19
*NO ONE* has any ideas?

---

### Post by kewlrichie on 2009-11-19
[http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10]("http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10")

see if that works out for you if not when I did it the guide semi-broken but I followed it up to the phamm part I got stuck and did a sudo apt-get dist-upgrade and went on from there so I had a 9.04 working and also added spam/virus scanning following falkos guides for a virtual domains using mysql on that same site. I just used the spam/virus and squirrelmail part also...give it a try it worked fine for me. If u need it I'll give u some help

---

### Post by abishur on 2009-11-19
Thanks, I see it is for setting up virtual hosting.  I've tried searching but I haven't really been able to find out what virtual hosting is, or why I should use it over non-virtual hosting.  Do you know?

---

### Post by kewlrichie on 2009-11-19
This is for virutal domians and users using LDAP as a backend

---

### Post by abishur on 2009-11-19
right... but my question was do you know why I should use it over a non-virtual domain (or virtual hosting as the link you provided calls it)?  What is the benefit of a virtual domain?  I had actually run into that very link several times in my hunt, but since I don't know anything about virtual domains I don't see any reason to use one.

---

### Post by kewlrichie on 2009-11-25
Well with that setup that i used from the howtoforge i think even if your going to use one domain i would still use that setup cause of the ease of using phamm to add virtual users so easily and set qoutas etc..

---

### Post by abishur on 2009-11-25
I feel like I'm not presenting my question right.  My question was do you know why I should use it over a non-virtual domain (or virtual hosting as the link you provided calls it)? What is the benefit of a virtual domain?

---

