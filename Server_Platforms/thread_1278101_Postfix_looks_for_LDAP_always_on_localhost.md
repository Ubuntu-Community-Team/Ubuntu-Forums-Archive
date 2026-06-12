---
title: "Postfix looks for LDAP always on localhost"
date: 2009-09-29
forum: Server Platforms
---

### Post by jakob42 on 2009-09-29
Hi guys,

I've installed a test mail server to try to connect postfix/cyrus to ldap. The openldap server runs on another host and is already populated for a PDC and other services. Cyrus is running and authenticating (with SASL/PAM) against the LDAP all right. But now I'm trying to get the virtual users running. I tried all kinds of configurations and postfix still wants only to connect to **localhast**. I trid hostname, ip address with ldap://, without...

```
root@paka2:~# cat /etc/postfix/virtual.ldap 
server_host = ldap://134.102.131.4
search_base = dc=taupo, dc=gsss, dc=uni-bremen, dc=de
port = 389
bind = no
version = 3
debuglevel = 10
query_filter = (|(mail=%s)(gosaMailAlternateAddress=%s))
result_attribute = uid, gosaMailForwardingAddress
special_result_attribute = member
```

```
root@paka2:/etc/postfix# postmap -q lenfers-test@bigsss-bremen.de ldap:virtual.ldap 
postmap: warning: dict_ldap_connect: Unable to bind to server ldap://localhost:389 as : -1 (Can't contact LDAP server)
```

I'm using Ubuntu 8.04, current postfix(-ldap) 2.5.1-2. And I really don't know what to try anymore...

TIA!

---

### Post by jakob42 on 2009-10-01
Found the solution, postmap needs a full path to the file, even if its in the current directory. Reason and more: [http://article.gmane.org/gmane.mail.postfix.user/202151](http://article.gmane.org/gmane.mail.postfix.user/202151)

---

