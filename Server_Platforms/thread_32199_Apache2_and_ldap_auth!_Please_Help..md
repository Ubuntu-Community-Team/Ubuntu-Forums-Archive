---
title: "Apache2 and ldap auth! Please Help."
date: 2005-05-06
forum: Server Platforms
---

### Post by Ric_ on 2005-05-06
](*,) 

Has anyone got a working config for apache2 and ldap authentification. I've tried various ways of doing it all i get is a repeated auth box asking me for user name and password. Any help would be great.

---

### Post by blueplazma on 2005-05-08
Can you check your Apache2 error log (probably /var/log/apache2/error.log) and tell use what you see there?  I've never personally tried this, but I imagine that it is possible.

---

### Post by Ric_ on 2005-05-09
Ok some more information if it helps.

Right this is my error log:

[Mon May 09 12:17:49 2005] [warn] [client 172.21.192.10] [30790] auth_ldap authenticate: user rharvey authentication failed; URI /blerk/ [ldap_simple        _bind_s() to check user credentials failed][Invalid credentials]

This is my config in the default apache site for now

<Directory "/var/www/blerk/">
 AllowOverride ALL
 AuthLDAPEnabled on
 AuthLDAPAuthoritative on
 AuthLDAPURL ldap://exchange2.pinnacle.co.uk
 AuthLDAPBindDN "CN=ldapquery, O=My Site PLC, C=GB"
 AuthLDAPBindPassword PASSWD_XXX
 AuthType Basic
 AuthName "Password Prompt"
 require valid-user
</Directory>

---

### Post by piedamaro on 2005-05-12
I didn't install it directly but the guy who configured it had to recompile ldap from source to make it work in because of some non-working schemas, he said.

---

### Post by Ric_ on 2005-05-13
Great thanks I'll give that a try, could you do me a hugh favour and post your apache conf (ldap part) on here too, it would be a great help!

Thanks in advance...

---

