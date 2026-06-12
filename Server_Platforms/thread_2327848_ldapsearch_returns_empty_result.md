---
title: "ldapsearch returns empty result"
date: 2016-06-15
forum: Server Platforms
---

### Post by Erik_Lunheim on 2016-06-15
Hi,
LDAP trouble...

If I do this search:
ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b "**ou=Limacute,dc=testing,dc=no**" mailAddr=test.account@test.no
**The result is emty.**

If I do this search:
ldapsearch -Q -LLL -Y EXTERNAL -H ldapi:/// -b "**dc=testing,dc=no**" mailAddr=test.account@test.no
**I'll get a hit:**
dn: uid=test.account,ou=People,domain=test.no,ou=Domains,ou=Limacute,dc=testing,dc=no
aksessId: 1189670281
antiVirus: filter
cn: test.account
domain: test.no
mail: [email]test.account@test.no[/email]
kundeNr: 62214
mailAddr: [email]test.account@test.no[/email]
mailDir: /home/brukere/bbnett.no/test.account
maildirQuota: 1000M
ordb: pass
status: ok
uid: test.account
userSpamAssassin: filter
vacation: 0
objectClass: limacuteConfig
objectClass: mailaccount
alias: test.account

If I delete one entry in LDAP, the search will work!
If I add a new account, the search will break!
I've reached some kind of limit....

Regards Erik

---

