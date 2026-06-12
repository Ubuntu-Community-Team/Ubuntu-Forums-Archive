---
title: "smbldap and password expired"
date: 2012-05-09
forum: Server Platforms
---

### Post by fluca1978 on 2012-05-09
Hi all,
I'm running server 11.04 and I keep my users locked out from the samba+ldap authentication since passwords expire every 3 months. Even if I try to run the following commands:

```
smbldap-usermod --shadowExpire "2020-12-31" $utente
        smbldap-usermod --shadowMax    "9999"       $utente
        smbldap-usermod -B 0                        $utente
        smbldap-usermod --sambaPwdMustChange 0      $utente
```

with *$utente* the target user, it seems that the password is unlocked but after 3 months the password is locked again, so the date 2020 is ignored, as well as the 99999.
AM I doing something wrong or is this a bug?

Thanks

---

### Post by fluca1978 on 2012-05-11
I've tested it on different installations and seems the problem is always the same. I suspect it is a PAM configuration, but I have no idea where to search for. Any suggestion?

---

### Post by fluca1978 on 2012-05-14
Has anybody experienced the same problem or is something wrong with my configuration?

---

### Post by fluca1978 on 2012-05-16
Seems to me also that *smbpasswd* can do the trick without requiring any *smbldap-passwd* management, but the periodic execution of *smbpasswd* is still required.

---

### Post by fluca1978 on 2012-05-16
I've also tried increasing the age of the password in the */etc/smbldap-tools/smbldap.conf* file:

```
defaultMaxPasswordAge="365"

```

but it seems it is not working. Any idea?

---

### Post by luvshines on 2012-05-20
> **fluca1978 said:**
> I've tested it on different installations and seems the problem is always the same. I suspect it is a PAM configuration, but I have no idea where to search for. Any suggestion?

If I understand correctly, your LDAP password for Samba keeps expiring after 3 months and you want to avoid it, correct ?

Did you check what all policies have been set under the sambaDomain(objectclass) for your sambaDomainName(domain account) on the LDAP server ?

---

### Post by fluca1978 on 2012-06-05
> **luvshines said:**
> If I understand correctly, your LDAP password for Samba keeps expiring after 3 months and you want to avoid it, correct ?

Did you check what all policies have been set under the sambaDomain(objectclass) for your sambaDomainName(domain account) on the LDAP server ?

You get it right, but can you please clarify what do you mean with "check the policies"?

---

