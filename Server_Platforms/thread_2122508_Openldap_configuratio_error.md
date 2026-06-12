---
title: "Openldap configuratio error"
date: 2013-03-05
forum: Server Platforms
---

### Post by rahuljanghel on 2013-03-05
Folks,

I am configuring my LDAP server following below manuals :
[https://help.ubuntu.com/12.04/serverguide/openldap-server.html](https://help.ubuntu.com/12.04/serverguide/openldap-server.html)
[https://help.ubuntu.com/12.04/serverguide/samba-ldap.html](https://help.ubuntu.com/12.04/serverguide/samba-ldap.html)
[https://help.ubuntu.com/12.04/serverguide/samba-dc.html](https://help.ubuntu.com/12.04/serverguide/samba-dc.html)

In short it is ubuntu 12.04, with samba 3.x and openldap.
now i am trying to authenticate users created with openVPN server.

OpenVPN has a nice web interface to configure LDAP authentication.
Setting are easy as below :

Primary server: 192.168.1.117
Bind DN: duffer
Base DN for User Entries : cn="duffer", cn="Users", dc="example", dc="com"
Username Attribute: 1005 {user duffer's uid as suggested on page}

Now while trying to authenticate another user account created in ldap database with normal permission getting below error :

LDAP exception on ldap://192.168.1.117/ (facility='admin_bind to  [duffer]'): {'info': 'invalid DN', 'desc': 'Invalid DN syntax'}:  auth/authldap:113,auth/authldap:280,ldap/ldapobject:207,ldap/ldapobject:422,ldap/ldapobject:426,ldap/ldapobject:432,ldap/ldapobject:96  (ldap.INVALID_DN_SYNTAX)

I tried with couple of change in DN parameter, but not luck.

Any help on this will be really appreciated. thanks.

~ Raul Janghel.

---

### Post by rahuljanghel on 2013-03-18
Help pls.

Rahul Janghel.

---

### Post by ranger12 on 2013-03-18
It appears as if you are creating a node for storing users in your ldap named Users. If so, than that should be ou=Users not cn=Users.
Take another look at the tutorial from the first linik you posted and look at the section marked **Modify/Populating Your Database**.
So I think that should be in your ldap as "cn=duffer,ou=Users, dc=example,dc=com". Also did  you setup your admin in your ldap as "duffer"?

---

