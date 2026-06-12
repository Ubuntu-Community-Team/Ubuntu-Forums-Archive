---
title: "Samba Domain Controller"
date: 2007-11-02
forum: Server Platforms
---

### Post by Joh_ on 2007-11-02
I'm having a seriously odd problem with samba as a domain controller. I can not - in what seems to be any way - assign a user as domain admin. 

Some outputs (with important bits in bold):

**id johan**
```

uid=1000(johan) gid=1000(johan) groups=1000(johan),107(admin),**1001(ntadmins)**
```
**net groupmap list**
```
Domain Users (S-1-5-21-762141134-348180756-486284822-513) -> domusers
Administrators (S-1-5-32-544) -> ntadmins
Domain Guests (S-1-5-21-762141134-348180756-486284822-514) -> nogroup
**Domain Admins (S-1-5-21-762141134-348180756-486284822-512) -> ntadmins**
Users (S-1-5-32-545) -> domusers
```
**pdbedit -Lv johan**
```

Unix username:        johan
NT username:
Account Flags:        [U          ]
User SID:             S-1-5-21-762141134-348180756-486284822-3000
**Primary Group SID:    S-1-5-21-762141134-348180756-486284822-513**
Full Name:            Johan SkÃ¶ld,,,
Home Directory:       \\snigeln\johan
HomeDir Drive:        H:
Logon Script:
Profile Path:         \\snigeln\profile\johan
Domain:               WOOD
Account desc:
Workstations:
Munged dial:
Logon time:           0
Logoff time:          never
Kickoff time:         never
Password last set:    fre, 02 nov 2007 23:34:02 CET
Password can change:  fre, 02 nov 2007 23:34:02 CET
Password must change: never
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
```

I'm ripping my hair off my head at the moment since I really can't find the problem. Any insight would be appreciated.

**EDIT:** I apparantly got it to work by doing nothing but deleting all the groups and re-adding them. Case closed. ;)

---

### Post by lenswipe on 2008-01-15
good for you im glad you got it working. Im havning problems getting samba to "domain control" check out my post maybe you can add some insight :D


Good Luck With ur Server... :D

---

