---
title: "Openldap offline authentication"
date: 2009-04-20
forum: Server Platforms
---

### Post by smythsys on 2009-04-20
Good afternoon,

             Does anybody now how to get offline authentication through LDAP in ubuntu 8.10? I've set up Openldap server and clients. However, when the network is down (can happen), the pcs can´t log in.
             Is there a way of "replicating" the ldap base on the clients via a cron job every so often?
             Or even like windows does, to let users who have logged in when the server was up, log on the computer. Via locally stored profiles or such. 

Thanks in advance.

---

### Post by smythsys on 2009-04-27
For any who has found this problem this works (not all is correct):

[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

The main point is this:

[https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto)

---

