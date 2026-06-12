---
title: "Password LDAP expires??"
date: 2009-05-28
forum: Server Platforms
---

### Post by eufran on 2009-05-28
Hello i have one Ubuntu server witch LDAP + Samba. 
And past time says "You can change inmediatily LDAP password".
But is only in LDAP, in Samba with Windows works fine.

How can i configure that passwords in ldap don´t expires?????

thaks

---

### Post by ghen on 2009-05-28
This is just a google search so it may or may not be correct.

For Samba:
[quote=http://www.linuxtopia.org/online_books/network_administration_guides/samba_reference_guide/18_passdb_23.html]sambaPwdMustChange 	Specifies the time (UNIX time format) when the user is forced to change his password. If this value is set to 0, the user will have to change his password at first login. If this attribute is not set, then the password will never expire.[/quote]

For OpenLDAP: (I think)
[quote=http://www.section6.net/wiki/index.php/Setting_up_OpenLDAP_for_Unix_Authentication]shadowExpire = -1

renders the account invalid until the next password change. To make the password never expire, set to 0. [/quote]
Do you use the command line or a GUI like webmin to access LDAP settings?

---

