---
title: "Apache2 + mod_auth_ldap problem"
date: 2005-12-08
forum: Server Platforms
---

### Post by super-user on 2005-12-08
Hi!

I have a Ubuntu Server running and want to setup apache to use ldap for authentication. The ldap server running is OpenLDAP. The main task at the moment is to authenticate webdav requests. For this I have the following setup:

```

# WebDAV:
Alias /webdav /xxx/www/ubiq/
<Directory /xxx/www/ubiq/>
         DAV On
         Order allow,deny
         Allow from all
         Options Indexes FollowSymLinks
         AllowOverride None
         AuthName "Ubiq Webdevelopers"
         AuthType Base
         AuthLDAPUrl ldap://localhost/dc=iwi?uid?sub"
         AuthLDAPBindDN "cn=admin,dc=iwi"
         AuthLDAPBindPassword "xxxxxxxx"
         require user ubiqdev
</Directory>

```

The DAV itself is working. I have tested it without authentication! But when I want to authenticate with ldap I get the following in my error log:

```

[crit] [client xxx] configuration error:  couldn't check user.  No user file?: /webdav

```

When I change logging to debug there is another message similar to this:

```

auth_ldap authenticate: ap_get_basic_auth_pw() returns -1

```

Does anyone have a clue?

---

### Post by gruepig on 2005-12-08
Here's what I have in a working apache2 config:

AuthType Basic
AuthName "foo"
AuthLDAPAuthoritative on
AuthLDAPEnabled on
AuthLDAPURL ldap://ldap/dc=example,dc=org?uid??ou=webusers
Require valid-user

Hope this helps.

---

### Post by Whizzy on 2005-12-09
join my forums today

[www.springshield.spreebb.com:D](www.springshield.spreebb.com:D)

---

### Post by super-user on 2005-12-09
Hi gruepig,

thanks for the reply. I have just tested this but I still get the same error. AFAIK AuthLDAPAuthoritative and AuthLDAPEnabled are "on" by default so it did not change anything.

Do you think it is possible that somehow my modules are broken? I checked the source file reporting that error and at the line throwing the error the LDAP module tries to get the password the user entered in the "ask pw" box. So the Apache does not recieve the password anyhow I try to connect!

Very strange!

---

