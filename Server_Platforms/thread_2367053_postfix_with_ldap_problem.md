---
title: "postfix with ldap problem"
date: 2017-07-25
forum: Server Platforms
---

### Post by no-pain-no-gain on 2017-07-25
I`ve try to set up a new mailgateway server with postfix. My Users are in Active Directory, so i`ve installed postfix and also postfix-ldap. But something is wrong:

I found in /var/log/mail.log.
```
postfix/smtpd[27051]: warning: ldap:/etc/postfix/maps/ldap_user.cf is unavailable. unsupported dictionary type: ldap
```

So I`ve checked:
```
postconf -m
btree
cidr
environ
fail
hash
inline
internal
memcache
nis
pipemap
proxy
randmap
regexp
socketmap
static
tcp
texthash
unionmap
unix

```

So it`s nomal that postfix has problems with ldap querys. 
I`ve also checked that i have not forgotten to install postfix-ldap:
```
sudo apt install postfix-ldap
[sudo] Passwort für mailadmin:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.
Statusinformationen werden eingelesen.... Fertig
»postfix-ldap« ist bereits die neuste Version (3.1.0-3).
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.
```

System is in german. The message means that postfix-ldap is already installed in the latest version. 

So I`m missing "something", but unfortunally i have no glue what. Hopefully you can help me 

Thanks

---

### Post by no-pain-no-gain on 2017-07-25
OK it was my fault. I`ve created a directory maps in /etc/postfix and moved everthing map related to this dierectory. Also the dynamicmaps.cf. 
After correcting the paths, postfix find the dynamicmaps.cf and is now able to do ldap querys as expected.

---

