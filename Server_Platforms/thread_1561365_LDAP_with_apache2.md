---
title: "LDAP with apache2"
date: 2010-08-26
forum: Server Platforms
---

### Post by mdfakkeer on 2010-08-26
i enabled LDAP authentication for group in apache2.2 is working fine.  When i enabled sub group search using AuthLDAPSubGroupDepth 1 is showing  error 


Invalid command 'AuthLDAPSubGroupDepth', perhaps misspelled or defined  by a module not included in the server configuration

here below the ldap coding for apache2 running in ubuntu 10.04

AuthzLDAPAuthoritative on
   AuthType Basic
   AuthName "xxxxx"
   AuthBasicProvider ldap

   AuthLDAPSubGroupDepth 1

   AuthLDAPBindDN "CN=Username,CN=Users,DC=domainname,DC=co,DC=in"
   AuthLDAPBindPassword password
   AuthLDAPURL  "ldap://ipaddressofserver:3268/DC=domainname,DC=co,DC=in?sAMAccountName?sub?(objectClass=*)"
   
   Require ldap-group CN=groupname,CN=Users,DC=domainname,DC=co,DC=in

i checked with enabling the authnz ldap. it is working.

#a2enmod authnz_ldap
Considering dependency ldap for authnz_ldap:
Module ldap already enabled
Module authnz_ldap already enable


  why the error showing. If any body knows please reply

---

