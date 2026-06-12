---
title: "Configure server use ldap authentication"
date: 2008-06-17
forum: Server Platforms
---

### Post by Phulerock on 2008-06-17
I want config samba openldap, use this document:
[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10-p2]("http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10-p2")
In step 9, I don't really understand the description of this step, do we need to configure our server to authenticate with openldap (as a option) ? If I don't do this step, whats next happen ?

---

### Post by erolleman on 2008-06-30
The reason you need to have the server itself authenticate to openLDAP is because linux handles the permissions.  Say you have a user "dood" in openLDAP that you log into samba with for access and you want to access a file.  Samba allows the login then tries to access the file with "dood"'s credentials, but linux will deny it because it can't find the user "dood" anywhere to determine if it has the appropriate permissions to access the file.  The reason it can't find the user account is because it needs to be configured to look through openLDAP for the account and his information (such as his uid number and group membership).

---

### Post by Phulerock on 2008-07-26
Greate, understood. Thank you so much.

---

