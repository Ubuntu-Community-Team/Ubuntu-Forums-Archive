---
title: "Reset openldap admin password on ubuntu 8.10"
date: 2009-01-30
forum: Server Platforms
---

### Post by c0rv1d on 2009-01-30
Hi all

I need set up our server environment on my local machine for code testing. We have openldap set up on our prod servers. Only thing is, I know nothing about openldap and how to configure it.

I did a sudo apt-get install slapd ldap-utils

I could recall that somewhere I was requested to enter my ldap admin password. But it seems like the password didn't get stored / is different because when I tried to run a shell script (written by someone from my company) to populate the LDAP directory and get prompted for my ldap password, I get: 
```

ldap_bind: Invalid credentials (49)
Error whilst loading LDAP data.  Halting.

```

Is there a way to reset the ldap admin password?

Sorry for not being clearer - my knowledge on (open)ldap is very limited.

By the way, I'm running XUbuntu 8.10 + openldap-2.4.11


Derek

---

### Post by JoeNazz on 2009-09-16
Have the same question.  Since slapd.conf never exist in new OpenLDAP versions I don't know where I can change the password if I have forgotten it. Anybody knows?

---

### Post by JoeNazz on 2009-09-16
Okay, I resolved it. Look in file /etc/ldap/slapd.d/cn=config/olcDatabase={0}config.ldif with attribute olcRootPW.

---

### Post by labiloute on 2011-04-18
> **JoeNazz said:**
> Okay, I resolved it. Look in file /etc/ldap/slapd.d/cn=config/olcDatabase={0}config.ldif with attribute olcRootPW.

Nice help for me on my debian squeeze !(after one week of intense research).
My olcRootPW attribute was in this file :
/etc/ldap/slapd.d/cn\=config/olcDatabase\=\{1\}hdb.ldif
Maybe it can help someones...

---

### Post by bloodymind on 2011-05-03
I have got ubuntu 10.10 MM
I can't find olcRootPW in /etc/ldap/slapd.d/cn=config/olcDatabase={0}config.ldif
does anyone know where is it?

---

### Post by dl7und on 2011-12-01
If you don't see it, then it's not there. I had the same problem. Just add a line

olcRootPW: secret

where secret is your password and you are good. But I better check if there is a way to hash this...

---

### Post by sebasto on 2012-02-13
> **dl7und said:**
> If you don't see it, then it's not there. I had the same problem. Just add a line

olcRootPW: secret

where secret is your password and you are good. But I better check if there is a way to hash this...

Hello

slappasswd is your new friend.
# slappasswd -s secret
(SSHA)<some funny characters>

Put the result in place of the clear password.
Restart slapd daemon.
Done. Password is encrypted in the config file.

---

### Post by dee1 on 2012-04-21
> **sebasto said:**
> Hello

slappasswd is your new friend.
# slappasswd -s secret
(SSHA)<some funny characters>

Put the result in place of the clear password.
Restart slapd daemon.
Done. Password is encrypted in the config file.

hello please I really need help! I have tried using slappasswd but I can't seem to figure out how it works.

the encrypted password is simply too long to be retyped and even when I did, I still got an error.

---

### Post by dee1 on 2012-04-21
Also any step by step instruction on how to get LDAP to recognise the password would really help thank you

---

### Post by dee1 on 2012-04-21
> **JoeNazz said:**
> Okay, I resolved it. Look in file /etc/ldap/slapd.d/cn=config/olcDatabase={0}config.ldif with attribute olcRootPW.

how did you copy and paste the long encrypted password, could you please explain the steps you used to resolve this issue? Its really giving me a headache right now. Thanks in advance.

---

