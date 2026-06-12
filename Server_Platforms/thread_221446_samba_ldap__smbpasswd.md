---
title: "samba ldap / smbpasswd"
date: 2006-07-23
forum: Server Platforms
---

### Post by oly on 2006-07-23
hi i have set up samba as a pdc with ldap but i am having problems with passwords they do not seem to be taken from ldap instead i have to run smbpasswd username to allow a user to login.

this directory will have around 800 users when complete and the ldap is also used for other authentication like to websites and other resources like jabber they all work fine it is only the windows login that needs smbpasswd.

i have two accounts working the root and nobody accounts but none of the others do they have the samba scheme on ll accounts but this does not help.

any ideas as to why or how i can find where the problem is the failed logins do not seem to be logged any where and the failure message for winodws is invalid username or password.

---

