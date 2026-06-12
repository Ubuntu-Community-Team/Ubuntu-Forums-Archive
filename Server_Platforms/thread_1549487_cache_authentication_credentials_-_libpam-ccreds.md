---
title: "cache authentication credentials - libpam-ccreds"
date: 2010-08-09
forum: Server Platforms
---

### Post by druhboruch on 2010-08-09
I would like to authenticate my laptop against LDAP server.

My setup works great when LDAP server is reachable.

I used the outdated howto: [https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto) to configure libpam-ccreds in lucid.

If I try to login with network down I am getting message:  You loged in using cashed credentials.
and then Authentication failure.

sudo cc_dump looks OK.

If your setup works, could you please post your /etc/pam.d/common-auth? 

Should I use pam-auth-update insted?

I am grateful for any hint or suggestion.

Thanks

---

### Post by druhboruch on 2010-08-13
...

---

### Post by nickpiggott on 2011-01-08
I have the same problem. I used pam-auth-update to configure PAM to include support for Kerberos, LDAP and Cached Credentials.

I think there is a bug in /etc/pam.d/common-account that it generates. The line:

```
account    [success=1 default=ignore]    pam_ldap.so
```will  always fail, because if the machine is off-line, it cannot contact the  LDAP server.

I have amended that line in my /etc/pam.d/common-account to read:

```
account    [success=1 authinfo_unavail=1 default=ignore]     pam_ldap.so 
```If the LDAP server cannot be reached, it now  proceeds as if it had succeeded.

There are some potential dangers to this approach, but it's a working solution for me.

---

