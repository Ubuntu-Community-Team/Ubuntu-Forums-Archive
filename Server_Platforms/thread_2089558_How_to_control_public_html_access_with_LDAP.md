---
title: "How to control public_html access with LDAP?"
date: 2012-11-29
forum: Server Platforms
---

### Post by borjamf on 2012-11-29
Im running Apache2 on Ubuntu 12.04 Server because I want to create a home directory for each ldap user. I'm using LDAP for authentication and NFS4 and it's working ok. Also I've done some tests with LDAP module for Apache2 and it's working ok.

The problem with this LDAP authentication is that any success login can access to ~user/public_html, even if the user is not the owner of that home.

I dont know how to control that, for example, userldap2 access to userldap1/public_html. I want that only the userldap1 access to userldap1.

Could anybody tell me how to control that with LDAP authentication?

I hope that you'll understand me.

My config (auth_ldap.conf)

 [<Directory /home/disco2/*/public_html>
  AuthName "Authentication"
  AuthType basic
  AuthBasicProvider ldap
  AuthzLDAPAuthoritative off
  AuthLDAPURL ldap://prueba.borja/dc=prueba,dc=borja?uid?
  Require ldap-filter objectClass=posixAccount
 </Directory>

---

### Post by borjamf on 2012-12-05
Im stuck on this. Anyone could help me?

---

