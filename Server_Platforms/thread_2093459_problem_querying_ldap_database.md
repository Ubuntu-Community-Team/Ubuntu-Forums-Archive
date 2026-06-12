---
title: "problem querying ldap database"
date: 2012-12-10
forum: Server Platforms
---

### Post by schnimmy on 2012-12-10
hi all, i´m running ubuntu 12.04 server, i installed openldap, tried querying the slapd-config database and received the following error:

```
root@host123:~# ldapsearch -Q -LLL -Y EXTERNAL ldapi:/// -b \
> cn=config olcDatabase={0}config olcAccess
ldap_sasl_interactive_bind_s: Unknown authentication method (-6)
    additional info: SASL(-4): no mechanism available: 
```i´m fairly new to this but from the error message it looked like there was a problem with binding using SASL which had been used okay in a few earlier queries no problem. I had no idea what to do so i tried restarting the slapd service, didn´t help. I then rebooted the machine repeated the query and it came back okay as follows

```

root@host123:~# ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b cn=config olcDatabase={0}config olcAccess
dn: olcDatabase={0}config,cn=config
olcAccess: {0}to * by dn.exact=gidNumber=0+uidNumber=0,cn=peercred,cn=external
 ,cn=auth manage by * break


```Can someone explain what happened, or at least how i could have diagnosed and solved the problem without simply rebooting? 

Thanks...

---

