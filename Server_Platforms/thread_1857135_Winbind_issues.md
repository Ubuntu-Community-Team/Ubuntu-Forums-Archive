---
title: "Winbind issues"
date: 2011-10-09
forum: Server Platforms
---

### Post by GTHvidsten on 2011-10-09
I have previously successfully followed [this howto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") to join my ubuntu server (10.04) to my AD.

Recently I had to reinstall my Windows server and therefore also reinstall the AD services. I successfully rejoined ubuntu to the AD with the "kinit" and "net ads join" commands, but the "wbinfo" commands just won't work!
This is so frustrating since I have obviously had all this work before with the same config files as I have now, but for some reason they won't work now.

```
# kinit Administrator@WHITESTONE.NO
Password for Administrator@WHITESTONE.NO: 

# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: Administrator@WHITESTONE.NO

Valid starting     Expires            Service principal
10/10/11 00:26:01  10/10/11 10:25:59  krbtgt/WHITESTONE.NO@WHITESTONE.NO
	renew until 10/11/11 00:26:01

# net ads join -U Administrator@WHITESTONE.NO
Enter Administrator@WHITESTONE.NO's password:
[2011/10/10 00:26:43,  0] libads/kerberos.c:333(ads_kinit_password)
  kerberos_kinit_password Administrator@WHITESTONE.NO@WHITESTONE.NO failed: Malformed representation of principal
Failed to join domain: failed to connect to AD: Malformed representation of principal

# net ads join -U Administrator           
Enter Administrator's password:
Using short domain name -- WHITESTONE
Joined 'JUPITER' to realm 'whitestone.no'

# wbinfo -t
checking the trust secret via RPC calls failed
Could not check secret

# wbinfo -u
Error looking up domain users
```

Since this has worked before I'm sure I'm only missing something trivial, but after an evening of googling and experimenting I just can't find a solution.
What could be wrong?

---

### Post by GTHvidsten on 2011-10-14
*Bump*

---

### Post by GTHvidsten on 2011-10-15
It seems I was finally able to get it to work again.
Here's what I found and did that fixed it:

[LIST]
[*]stop *smbd*, *nmbd* and *winbindd* (make sure they are really dead using *ps*. *winbindd* still lingered after I stopped the service)
[*]delete the samba from the PDC (using the Management Console)
[*]delete the secrets database (*/var/lib/samba/secrets.tdb*)
[*]join the domain again
[*]start the daemons again (*smbd*, *nmbd* and *winbindd*)
[/LIST]

---

