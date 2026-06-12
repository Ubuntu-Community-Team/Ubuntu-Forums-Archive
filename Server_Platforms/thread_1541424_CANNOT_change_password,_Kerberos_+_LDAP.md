---
title: "CANNOT change password, Kerberos + LDAP"
date: 2010-07-29
forum: Server Platforms
---

### Post by proge on 2010-07-29
I have installed servers(10.04 LTS Server) with Kerberos + LDAP, now I can ssh to all those servers and login with kerberos principle. But when I want to change password, I got such error:
```
Current Kerberos password:
Enter new Kerberos password:
Retype new Kerberos password:
Password change rejected: Password not changed.
Kerberos database constraints violated while trying to change password.

passwd: Authentication token manipulation error
passwd: password unchanged
```

I have search this issue but cannot any useful information. Would someone give me a direction?

---

### Post by proge on 2010-07-30
I found something in the KDC server, is this a bug of kerberse change password service?
```
Jul 30 18:10:19 server1 krb5kdc[1162]: AS_REQ (4 etypes {18 17 16 23}) 172.16.40.25: NEEDED_PREAUTH: proge@MYCOMPANY.COM for kadmin/changepw@MYCOMPANY.COM, Additional pre-authentication required
Jul 30 18:10:19 server1 krb5kdc[1162]: AS_REQ (4 etypes {18 17 16 23}) 172.16.40.25: ISSUE: authtime 1280484619, etypes {rep=18 tkt=18 ses=18}, proge@MYCOMPANY.COM for kadmin/changepw@MYCOMPANY.COM
Jul 30 18:10:26 server1 kadmind[1114]: chpw request from 172.16.40.25 for proge@MYCOMPANY.COM: User modification failed: Strong(er) authentication required
```

---

