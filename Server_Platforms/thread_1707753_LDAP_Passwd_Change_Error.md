---
title: "LDAP Passwd Change Error?"
date: 2011-03-15
forum: Server Platforms
---

### Post by KyleSo on 2011-03-15
SOLVED!

Ok, I recently set up a LDAP server, and have a server using it to authenticate users. That works completely, but when a user tries to use passwd to change his password this happens. 

```

kyle@ruby:~$ passwd
Enter login(LDAP) password: 
passwd: Authentication information cannot be recovered
passwd: password unchanged
kyle@ruby:~$
```And this is in /var/log/auth.log
```

Mar 15 20:09:53 ruby passwd[1827]: pam_unix(passwd:chauthtok): user "kyle" does not exist in /etc/passwd
Mar 15 20:09:54 ruby passwd[1827]: pam_unix(passwd:chauthtok): user "kyle" does not exist in /etc/passwd

```

---

### Post by KyleSo on 2011-03-16
Solution:
Changed all of /etc/pam.d/common-password to
```
password   sufficient   pam_ldap.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5
```

---

