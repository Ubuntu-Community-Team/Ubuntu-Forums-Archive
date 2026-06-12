---
title: "Apache 2.2 ldap authentication port on Hardy 64 bit"
date: 2008-10-20
forum: Server Platforms
---

### Post by jw012n5611 on 2008-10-20
On a 32 ubuntu system this .htaccess file works fine:
AuthLDAPURL "ldap://gc.campus.aston.ac.uk:3268 /ou=people,dc=campus,dc=aston,dc=ac,dc=uk?cn?sub"
Require valid-user
AuthzLDAPAuthoritative on
AuthLDAPBindDN "CN=ldapproxy,CN=Users,DC=campus,DC=aston,DC=ac,DC=uk"
AuthLDAPBindPassword "******"
Require valid-user

On a 64 bit system (I've tried 2 servers) it fails with
[Mon Oct 20 19:52:35 2008] [warn] [client 82.46.200.11] [7022] auth_ldap authenticate: user williamj authentication failed; URI /p2 [LDAP: ldap_simple_bind_s() failed][Can't contact LDAP server]

but this syntax, not using the port works fine:
AuthLDAPURL "ldap://gc.campus.aston.ac.uk/ou=people,dc=campus,dc=aston,dc=ac,dc=uk?cn?sub"
Require valid-user
AuthzLDAPAuthoritative on
AuthLDAPBindDN "CN=sparta,OU=s,OU=People,DC=campus,DC=aston,DC=ac,DC=uk"
AuthLDAPBindPassword "*******"
Require valid-user

it fails if the port is set to 389.  Any solutions welcome.

---

### Post by lykwydchykyn on 2008-10-20
If it works fine when you don't specify a port, can you run a packet sniffer and see what port it's using?

---

