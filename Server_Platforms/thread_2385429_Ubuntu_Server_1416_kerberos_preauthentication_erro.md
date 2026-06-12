---
title: "Ubuntu Server 14/16 kerberos preauthentication error"
date: 2018-02-20
forum: Server Platforms
---

### Post by vinigobbi on 2018-02-20
Hi, i'm using my ubuntu server to join in my windows domain, so i have my samba managed by my windows groups. Everything is working fine but every 3-5 days, i'm getting this error:


kerberos_kinit_password failed preauthentication failed






kerberos_kinit_password [EMAIL="S0VLFS070@SISTEMA.COM.BR"]S0VLFS070@SISTEMA.COM.BR[/EMAIL] failed: Preauthentication failed


Join to domain is not valid: Logon  failure




So, i have to run this commands:


kinit [EMAIL="administrador@SISTEMA.COM.BR"]administrador@SISTEMA.COM.BR[/EMAIL]
net ads join -U administrador


After that, everything backs to normal.




This problem occurs when i'm running ubuntu server 14 or ubuntu server 16.
I have an old ubuntu server 12 who dont have this problem. The problem is i can't install a new ubuntu server 12 because the packs isn't available anymore.


Any ideas?

---

