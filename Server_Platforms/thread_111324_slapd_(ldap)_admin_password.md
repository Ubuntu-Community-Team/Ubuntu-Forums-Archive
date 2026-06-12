---
title: "slapd (ldap) admin password"
date: 2006-01-02
forum: Server Platforms
---

### Post by chele on 2006-01-02
Where does slapd store it's own admin password? I have installed the package using apt-get, it appears to be running, but I cannot administrate it as it does not accept the password I entered for in when it was installed. A lot of the docs I have seen show it stored in the slapd.conf file, but there is no password entry there in this installation.

---

### Post by chele on 2006-01-02
> $ ldapadd -D 'dc=local' -f contact.ldif
SASL/DIGEST-MD5 authentication started
Please enter your password:
ldap_sasl_interactive_bind_s: Internal (implementation specific) error (80)
additional info: SASL(-13): user not found: no secret in databaseThis is the error I get when I try to add data to the base.

---

### Post by bluefrog on 2006-01-02
in /etc/ldap.secret. the password has to be written in clear (no hash)
then chmod 600 /etc/ldap.secret.

sry was thinking about samba-ldap. don't about ldap alone, have a look anyway...

james

---

### Post by chele on 2006-01-02
[quote=bluefrog]in /etc/ldap.secret. the password has to be written in clear (no hash)
then chmod 600 /etc/ldap.secret.[/quote]No luck :-(

There was not an /etc/ldap.secret file, so I created one, with the clear text password as the only content. Same difference. No go.

You are correct that there is no samba involved at this point. I am just trying out a bare ldap setup still.

---

### Post by chele on 2006-01-02
This works:```
~$ ldapadd -D 'cn=admin,dc=local' -f contact.ldif -x -W
```

---

