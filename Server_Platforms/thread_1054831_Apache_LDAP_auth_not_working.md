---
title: "Apache LDAP auth not working"
date: 2009-01-30
forum: Server Platforms
---

### Post by nocturn on 2009-01-30
I'm trying to get Apache to do LDAP authentication on my Hardy server.
LDAP is in use and working for anything from logins to Zarafa and Drupal.

But, with my configuration, it fails for Apache and I do not even see connections coming in on the LDAP server.

Apache Vhost is defined like this:

```
<VirtualHost *>
        ServerName ***
        DocumentRoot /storage/ftp/
        <Directory /storage/ftp/>
                AuthBasicProvider ldap
                AuthzLDAPAuthoritative off
                AuthType Basic
                AuthName "Login"

                AuthLDAPURL "ldap://localhost:389/ou=People?uid"
                AuthLDAPBindDN "***"
                AuthLDAPBindPassword "***"
                AuthLDAPGroupAttribute memberUid

                Require valid-user

                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

</VirtualHost>
```

Note that my LDAP allows anomymous queries too, but it doesn't work with that either.

Any idea of what I can be doing wrong?

---

