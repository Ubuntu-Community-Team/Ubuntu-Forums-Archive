---
title: "&quot;ibmuser&quot;"
date: 2012-10-01
forum: Security
---

### Post by mike acker on 2012-10-01
re: "do not tamper with root password"

It occurred to me maybe we should simply change the root password for security reasons:

if every copy of Ubuntu is distributed with the same root password then it is reasonable to presume that the hackers know what that is set to

just as in the days of IBM System/370 : the default password was "IBMUSER".  We were instructed to change that as soon as we had established our administrator account(s).

~~~
I recently installed a Cisco wireless router.  The CD that came with the router connected my PC to the router -- via  wireless -- using the same sort of standard "getting started" password.

it allowed me to change those settings during the configuration -- but did not insist on that being done :( .it would be far better to require an RJ45 connection during initial configuration -- or any reset of the security password (WPA2-PSK).

~~~
so my question this morning: is each copy of Ubuntu given a unique password for root -- or does this old default password vulnerability still haunt us ?

---

### Post by albandy on 2012-10-01
root account is disabled by default, there is no password assigned.

---

### Post by oldos2er on 2012-10-01
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by mike acker on 2012-10-01
> **albandy said:**
> root account is disabled by default, there is no password assigned.

cool. that is what we were supposed to do with "IBMUSER" -- delete or disable.

---

