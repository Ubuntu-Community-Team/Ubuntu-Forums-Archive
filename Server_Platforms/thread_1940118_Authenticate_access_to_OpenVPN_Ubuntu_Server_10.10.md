---
title: "Authenticate access to OpenVPN Ubuntu Server 10.10 through  AD 2008"
date: 2012-03-13
forum: Server Platforms
---

### Post by Felipe Viveros on 2012-03-13
Hello everybody, I'm having trouble completing a task:

 I have to authenticate access to openvpn (Ubuntu server installed 10.10) using some users created in Active Directory 2008. within the openvpn console, I set up access through LDAP. set up the primary ip as the server ip Win2k8 server, when I try to log in using the data of one of the accounts created it gives me:access denied.

 this is the report:

LDAP exception on ldap://172.31.1.7/ (facility='search ('CN=Users,  DC=example, DC=net', 2,  '(sAMAccountName=fviveros@ims\\2elam\\2eco\\2emz)')'): {'info':  '000004DC: LdapErr: DSID-0C0906DD, comment: In order to perform this  operation a successful bind must be completed on the connection., data  0, v1772', 'desc': 'Operations error'}:  auth/authldap:119,ldap/ldapobject:496,ldap/ldapobject:422,ldap/ldapobject:426,ldap/ldapobject:432,ldap/ldapobject:96  (ldap.OPERATIONS_ERROR

---

### Post by RyanRahl on 2012-03-20
I'm pretty sure you have to set up encryption keys for your users in VPN. I've never heard of authentication to OpenVPN with AD users or LDAP. Then again I have never heard of "OpenVPN Console" so I could be off base. This tutorial is probably the best place for you to start:

[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

---

