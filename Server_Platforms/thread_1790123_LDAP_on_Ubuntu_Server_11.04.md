---
title: "LDAP on Ubuntu Server 11.04"
date: 2011-06-24
forum: Server Platforms
---

### Post by lingenthron on 2011-06-24
Is it even possible to use LDAP on Ubuntu 11.04?  After a full day of googling, every guide I can find is either for another version of Ubuntu or is horribly broken (including the official docs).  Has anyone successfully managed to do this, and how?

---

### Post by ruffEdgz on 2011-06-24
I'm not using natty for my server but did a quick package search online and found it can be downloaded. If that is the case then making an LDAP server on natty can be done:

[http://packages.ubuntu.com/natty/slapd](http://packages.ubuntu.com/natty/slapd)

With that in mind, I looked over the Ubuntu Help documentation on OpenLDAP and didn't see anything out of the ordinary that would be any different between versions (10.04 to 11.04). Here is the document: [https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

### Post by Mekik on 2011-06-27
i am successfully managed to install openldap under ubuntu 11.04 on server x64. Just follow steps mentioned in official documentation found at [https://help.ubuntu.com/11.04/index.html](https://help.ubuntu.com/11.04/index.html) . EXCEPT following command (please do not perform following command):-
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/cosine.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/nis.ldif
sudo ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/ldap/schema/inetorgperson.ldif

because by default those schema are included inside slapd.conf.

cheers.... :)

---

