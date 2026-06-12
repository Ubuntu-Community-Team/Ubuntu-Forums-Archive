---
title: "OpenLDAP + Apache: Anonymous bind can't find user"
date: 2014-02-21
forum: Server Platforms
---

### Post by DarkMorford on 2014-02-21
I'm trying to set up OpenLDAP as an authentication backed for my Apache server. OpenLDAP appears to be configured correctly, as I can search anonymously from the command line and find a user.
```
smorford@web:~$ ldapsearch -x -L -H ldap://192.168.0.254 -b dc=example,dc=com uid=smorford
version: 1

#
# LDAPv3
# base <dc=example,dc=com> with scope subtree
# filter: uid=smorford
# requesting: ALL
#

# smorford, users, example.com
dn: uid=smorford,ou=users,dc=example,dc=com
cn: Shawn Morford
uid: smorford

# search result

# numResponses: 2
# numEntries: 1
```

However, I can't get Apache to authenticate. I put together a simple .htaccess file in a subdirectory just for testing:
```
AuthType basic
AuthName "LDAP-protected folder"
AuthBasicProvider ldap
AuthLDAPUrl ldap://192.168.0.254/dc=example,dc=com?uid?sub
Require ldap-user smorford
```

When I attempt to access the folder, I'm prompted for my credentials as expected, but I'm never actually granted access. I turned LogLevel up to 'debug' in my VirtualHost, tried again, and then looked in the Apache error log. What I found there boggles the mind.
```
[Fri Feb 21 19:24:57 2014] [debug] mod_authnz_ldap.c(1016): [17430] auth_ldap url parse: `ldap://192.168.0.254:389/dc=example,dc=com?uid?sub', Host: 192.168.0.254, Port: 389, DN: dc=example,dc=com, attrib: uid, scope: subtree, filter: (null), connection mode: not using SSL
[Fri Feb 21 19:24:57 2014] [debug] mod_authnz_ldap.c(403): [client 192.168.0.11] [17430] auth_ldap authenticate: using URL ldap://192.168.0.254:389/dc=example,dc=com?uid?sub
[Fri Feb 21 19:24:57 2014] [info] [client 192.168.0.11] [17430] auth_ldap authenticate: user smorford authentication failed; URI /~smorford/ldap/ [User not found][No such object]
[Fri Feb 21 19:24:57 2014] [error] [client 192.168.0.11] user smorford not found: /~smorford/ldap/
```

I know the user exists in OpenLDAP, because I can find it anonymously with ldapsearch. What's more, if I configure Apache to bind with the database's rootDN it grants access without a hitch. What am I missing that's screwing up Apache's search?

---

