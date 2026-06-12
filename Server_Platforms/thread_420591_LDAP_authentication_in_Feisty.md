---
title: "LDAP authentication in Feisty"
date: 2007-04-23
forum: Server Platforms
---

### Post by Bwosc on 2007-04-23
I followed the community tutorials for making LDAP Client Authentication (for U6.10), but the GDM login says that the username or the password is wrong (but everything else works). Maybe I forgot something with MD5 authentication so that the server gets the password in cleartext instead in MD5 hash?

Has anybody else tried LDAP authentication in the new Feisty Fawn?

---

### Post by namxam on 2007-04-24
Well, my problem is that the mod_auth_ldap seems to be left out of the feisty realease, so there is no ldap authentication possible at all (at least for apache 2.2.*). Is that correct?

---

### Post by Bwosc on 2007-04-25
I managed to authenticate on the upgraded client (from 6.10) but the new one denies that username even exists! Very strange, very strange...

---

