---
title: "nextcloud from snap 18.04"
date: 2018-11-23
forum: Server Platforms
---

### Post by automaton2 on 2018-11-23
Attempting to use nextcloud from snap with LDAP auathentication, is fine for LDAP on 389, but fails on LDAP with 636.

The failure appears to be the private cert used for LDAPS, and that the nextcloud snap does not read the defaul ldap.conf to define a private root cert.

Any suggestions on how to specify a private root cert for the nextcloud snap to use for LDAPS would be appreciated.

---

