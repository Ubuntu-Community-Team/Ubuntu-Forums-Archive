---
title: "Samba PDC and access denied errors"
date: 2014-05-21
forum: Server Platforms
---

### Post by karaluh on 2014-05-21
Hello,
I'm trying to replace NT 4.0 PDC with Samba. I used this howto:

[http://www.enterprisenetworkingplanet.com/netos/article.php/3457461/Replace-Your-NT4-Domain-Controller-with-Samba-3-Part-2.htm](http://www.enterprisenetworkingplanet.com/netos/article.php/3457461/Replace-Your-NT4-Domain-Controller-with-Samba-3-Part-2.htm)

and it looked like the migration completed successfully. When I try to join a computer I get Access Denied error messages, so I went back to the Ubuntu Samba howto

[https://help.ubuntu.com/10.04/serverguide/samba-dc.html](https://help.ubuntu.com/10.04/serverguide/samba-dc.html)

and it turned out I didn't have "machines" group. After creating it and trying to apply the next step:
```
sudo net rpc rights grant "MYDOMAIN\Administrator" SeMachineAccountPrivilege SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege SeRemoteShutdownPrivilege
```
I also got Access Denied error. It asks me root password, and since it is disabled I tried -U Administrator but I got the same error. What should I do next?

---

### Post by karaluh on 2014-06-27
OK, I repopulated the LDAP database and everything there is looking OK, but the Access Denied error is still there. This time however Samba gives an error in the logs:
> User Administrator in passdb, but getpwnam() fails! I googled it, but none of the solutions worked.

---

### Post by karaluh on 2014-06-27
OK, forget the Administrator issue, I can use root or sudoer and I don't have the above error. Access denied however persists. This time samba log gives:
> Error writing 4 bytes to client, -1. (Transport endpoint is not connected) 

---

