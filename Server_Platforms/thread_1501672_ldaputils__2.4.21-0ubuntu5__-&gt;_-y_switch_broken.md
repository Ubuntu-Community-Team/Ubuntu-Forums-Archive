---
title: "ldaputils  2.4.21-0ubuntu5  -&gt; -y switch broken on ldapsearch, ldapadd"
date: 2010-06-04
forum: Server Platforms
---

### Post by uslacker99 on 2010-06-04
The -y switch appears to be broken on the ldapsearch and ldapadd binaries. I'm using Ubuntu 10.04 


root@zangief:~# uname -a
Linux zangief 2.6.32-22-server #35-Ubuntu SMP Tue Jun 1 15:34:46 UTC 2010 x86_64 GNU/Linux

root@zangief:~# dpkg -S ldapsearch
ldap-utils: /usr/share/man/man1/ldapsearch.1.gz
ldap-utils: /usr/bin/ldapsearch

root@zangief:~# dpkg -l ldap-utils
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  ldap-utils                2.4.21-0ubuntu5           OpenLDAP utilities

Here's an example:
root@zangief:~# echo "secret" > ~/test
root@zangief:~# /usr/bin/ldapsearch -y ~/test -D "uid=zimbra,cn=admins,cn=zimbra" -xH ldap://shaokahn.shocknetwork.com -b 'dc=shocknetwork,dc=com' objectclass=*
Warning: Password file /root/test is publicly readable/writeable
ldap_bind: Invalid credentials (49)

root@zangief:~# /usr/bin/ldapsearch -w secret -D "uid=zimbra,cn=admins,cn=zimbra" -xH ldap://shaokahn.shocknetwork.com -b 'dc=shocknetwork,dc=com' objectclass=*
# extended LDIF
#
# LDAPv3
# base <dc=shocknetwork,dc=com> with scope subtree
# filter: objectclass=*
# requesting: ALL
#
...

---

