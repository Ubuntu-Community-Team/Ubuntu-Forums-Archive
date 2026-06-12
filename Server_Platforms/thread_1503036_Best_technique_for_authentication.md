---
title: "Best technique for authentication?"
date: 2010-06-06
forum: Server Platforms
---

### Post by free-radical on 2010-06-06
Hello,

I try to install a server based on Ubuntu. It will provide many different services as SMTP,IMAP,Jabber,SVN(via Apache),maybe a groupware and some other web applications.

I'm looking for a way of authenticating the same set of users (a user essentially has a username, a domain it is belonging to and some passwords) against all of the services.

What is the most flexible and elegant way? I need a method which is not too bloated (mysql or ldap would be okay) and is easily applyable to all those services and all services which maybe will come later.

I've read some documentation about sasl, mysql-authentication, ldap-authentication, pam, cyrus, apache, ... and i'm somewhat confused now :confused: about the proper way.

For now I suspect MySQL to be the best method for that, but i'm not sure about the flexibility for embedding it into all the services.

I hope for any clarifying comments about that.

Thank you ;)

---

### Post by HermanAB on 2010-06-06
If you have many servers and many users, take your pick from:
NIS - an oldie but a goodie
LDAP - slightly newer and overhyped in its heyday
PAM MySQL - the flavour of the month

If however you have only one server, then you should keep it simple and make a system account for each user.

---

