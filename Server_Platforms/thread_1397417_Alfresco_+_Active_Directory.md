---
title: "Alfresco + Active Directory"
date: 2010-02-03
forum: Server Platforms
---

### Post by namdung on 2010-02-03
Just installed Alfresco 3.2 using the Canonical repo in Karmic. Unable to find proper guide to enable Active Directory authentication.
Help please!!!

---

### Post by R.Bucky on 2010-02-03
[http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/]("http://buckycomputing.net/blog/how-to-join-ubuntu-to-microsoft-active-directory-domain-using-likewise-open/")

---

### Post by namdung on 2010-02-03
Actually needed to authenticate users in Alfresco from Active Directory.

---

### Post by koenn on 2010-02-04
[http://wiki.alfresco.com/w/images/6/62/Installing_and_Configuring_Alfresco_ECM_Community_Edition_3_2_r2.pdf](http://wiki.alfresco.com/w/images/6/62/Installing_and_Configuring_Alfresco_ECM_Community_Edition_3_2_r2.pdf)

(from [http://wiki.alfresco.com/wiki/Main_Page](http://wiki.alfresco.com/wiki/Main_Page) )

page 74 and following

"pass-through" authentication is not true AD authentication, but it probably does what you're looking for.

else, look at LDAP auth and Kerberos auth (possibly chained)

---

