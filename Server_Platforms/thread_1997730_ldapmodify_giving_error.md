---
title: "ldapmodify giving error"
date: 2012-06-05
forum: Server Platforms
---

### Post by fabiorochapt on 2012-06-05
Hey guys,

Im trying to set up ubuntu server mostly for media share. Im a newbie so im following carefully a tutorial.

Everything seems to going well until i found a problem:

[http://ubuntuforums.org/showthread.php?t=1683595](http://ubuntuforums.org/showthread.php?t=1683595)

This is the tutorial.

My samba_indexes.ldif looks like this:

```
dn: olcDatabase={1}hdb,cn=config
changetype: modify
add: olcDbIndex
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: uid eq,pres,sub
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub
```

Then im supposed to type: ldapmodify -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f samba_indexes.ldif

This is the output @ putty:

```
root@Webserver:/usr/bin# ldapmodify -Y EXTERNAL -H ldapi:/// -D cn=admin,cn=config -W -f samba_indexes.ldif
Enter LDAP Password:
SASL/EXTERNAL authentication started
SASL username: gidNumber=0+uidNumber=0,cn=peercred,cn=external,cn=auth
SASL SSF: 0
ldapmodify: invalid format (line 1) entry: ""
```

Any help would be really appreciated.

Thanks in advance

---

