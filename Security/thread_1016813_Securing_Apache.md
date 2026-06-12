---
title: "Securing Apache"
date: 2008-12-20
forum: Security
---

### Post by speedsix on 2008-12-20
I want to auto allow any connection from the internal network i.e 10.0.0.* but prompt for a password externally.

Now I have it configured to prompt for a password currently which works but I want to modify this to auto-allow internal connections.

```
    
    #AuthType           Digest
    #AuthName           "MythTV"
    #AuthUserFile       /etc/mythtv/mythweb-digest
    #Require            valid-user
    #BrowserMatch       "MSIE"      AuthDigestEnableQueryStringHack=On
    #Order              allow,deny
    #Satisfy            any
    
    Order deny,allow
    Deny from all
    AuthName "Mythweb"
    AuthUserFile /etc/mythtv/mythweb-digest
    AuthType Digest
    Require valid-user
    Allow from 10.0.0.4
    Satisfy Any

```


The commented out section is just a password, the lower portion is what I changed it to after a bit of googling. This allows the 10.0.0.4 connection and does actually prompt for a password externally but the password is always refused. Any ideas why?

---

