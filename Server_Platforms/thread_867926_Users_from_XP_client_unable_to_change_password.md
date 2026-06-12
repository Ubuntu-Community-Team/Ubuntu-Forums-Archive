---
title: "Users from XP client unable to change password"
date: 2008-07-23
forum: Server Platforms
---

### Post by shizakapayou on 2008-07-23
I've setup a domain using Ubuntu Server 8.04 as the PDC, following rickyjones' guide: [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

So far, everything is working well.  DNS works great, XP can join the domain easily, users can log in and access shares which are automatically mapped, and the file server permissions have been set.  My one issue is allowing users to change their own password from Windows.  I've setup several users, and none, including members of the Domain Admins group, are allowed to change their password from an XP client machine.  From the server, I have no problem using smbldap-passwd to change it for them.

Googling about, I've found that this should be the relevant section of slapd.conf.  I've tried several different combinations and none have worked yet.

```
# The userPassword by default can be changed
# by the entry owning it if they are authenticated.
# Others should not be able to see it, except the
# admin entry below
# These access lines apply to database #1 only

access to attrs=userPassword,shadowLastChange,sambaNTPassword,sambaLMPassword
        by dn="cn=admin,dc=dci,dc=local" write
        by anonymous auth
        by self write
        by * none

```

I'm about to setup an Ubuntu VM and attempt joining it.  However, most of my users run Windows so I need them to be able to change.  Any ideas?

---

