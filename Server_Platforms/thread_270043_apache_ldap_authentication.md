---
title: "apache ldap authentication"
date: 2006-10-02
forum: Server Platforms
---

### Post by theycallmepj on 2006-10-02
I am working on moving my web server from fedora core 4 to ubuntu server.

We have a secure login and it uses ldap to authenticate users. I tried to copy the same bit of code from the old server to the new....i know that I am putting it in the correct place, I get this error on ubuntu when i restart apache



Here is the old bit of code
```
<Directory "/www/html_secure">

    Options Indexes Includes FollowSymLinks ExecCGI

    AllowOverride All
    Order allow,deny
    Allow from all

AuthType Basic
AuthName "Secure Area"

require valid-user

AuthLDAPBindDN "cn=LookUp,ou=People,dc=masd,dc=edu"
AuthLDAPBindPassword masdsearch
AuthLDAPAuthoritative off
AuthLDAPCompareDNOnServer On
AuthLDAPURL ldap://server1.masd.edu/ou=People,dc=masd,dc=edu?sAMAccountName


</Directory>
```
That works on fedora core 4

this is the error I get in ubuntu when I restart apache

```
Syntax error on line 32 of /etc/apache2/sites-enabled/site-ssl:
Invalid command 'AuthLDAPBindDN', perhaps mis-spelled or defined by a module not included in the server configuration
```


Any ideas? I did an exact copy and paste

---

### Post by spierepf on 2007-11-08
ubuntu doesn't install the mod_authz_ldap module by default. You'll need something like:

$ sudo a2enmod authnz_ldap

Hope that helps.

---

