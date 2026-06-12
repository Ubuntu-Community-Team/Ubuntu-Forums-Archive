---
title: "Apache 2 mod_auth_ldap"
date: 2005-11-14
forum: Server Platforms
---

### Post by heisters on 2005-11-14
I'm trying to setup LDAP authentication over SSL. Unencrypted LDAP works fine. When I enable SSL by doing ldaps:// I get this error in the Apache error log:
```
LDAP: ssl connections not supported
```Since the packaged mod_auth_ldap is for Apache 1.3, I thought I'd build Apache 2 from source, and maybe that could give me mod_auth_ldap with SSL support. However, upon apt-getting the Apache 2 source, it looks like SSL is enabled in the rules file.

Is the error I'm getting accurate? Could this be due to a configuration error, rather than an actual build-support error?

---

