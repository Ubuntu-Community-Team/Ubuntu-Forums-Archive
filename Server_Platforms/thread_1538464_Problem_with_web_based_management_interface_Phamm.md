---
title: "Problem with web based management interface Phamm"
date: 2010-07-25
forum: Server Platforms
---

### Post by vl72 on 2010-07-25
Hello!
I try to install web based management interface Phamm from this HOWTO
[http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10](http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-pop3-imap-on-ubuntu-8.10)
[http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10](http://www.howtoforge.com/postfix-virtual-hosting-with-ldap-backend-and-with-dovecot-as-imap-pop3-server-on-ubuntu-karmic-koala-9.10)  ,
but when I've typed [http://server01/phamm](http://server01/phamm) and have logined to my LDAP backend with my account cn=admin,dc=local,dc=net I've seen only 2 black lines and "logout  cn=admin,dc=local,dc=net" :(.
I've downloaded next packages 
phamm_0.5.12-4_all.deb,
phamm-ldap_0.5.12-4_all.deb,
phamm-ldap-amavis_0.5.12-4_all.deb,
phamm-ldap-vacation_0.5.12-4_all.deb.
from [http://packages.ubuntu.com/jaunty/](http://packages.ubuntu.com/jaunty/) for my Ubuntu server 9.04.
I've decided to configure my LDAP server with help /etc/ldap/slapd.conf, so I've changed   in /etc/default/slapd line 
SLAPD_CONF="" 
and replaced it with  
SLAPD_CONF=/etc/ldap/slapd.conf
It's easy for me then convert the schema and another files to ldif files and
I can use web interface "Webmin" as a program so can manage my server.
I've  configured my LDAP (Openldap), Postfix and Dovecot  servers, install and configured gnarwl ( see below). My mail server ( Postfix and Dovecot) work now. 
What's wrong in my configuration?
Maybe I haven't need packages or wrong permissions.
What do you think?
Can anybody help me?

---

### Post by mark1124 on 2010-07-25
I recently stumbled across [The Dedicated Server Handbook]("http://www.thededicatedserverhandbook.com/"), which is a great resource for learning to manage your own linux server.  The book covers everything from setting up DNS, websites, email, databases to analyzing your local webstats with Webalizer.

You should get [The Dedicated Server Handbook]("http://www.thededicatedserverhandbook.com/") now!

I almost forgot - there's a free video series in addition to the ebook - the video series on its own is gold.  I highly recommend you sign up for that, at the very least.

---

