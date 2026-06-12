---
title: "Samba PDC w/ LDAP backend -- can't add computer to the domain"
date: 2008-12-22
forum: Server Platforms
---

### Post by troyready on 2008-12-22
Hello everyone! I'm really excited about transforming my little Samba fileserver into a full-fledged domain controller with a LDAP backend, but I can't add any machines to the domain :(

I followed the 7.10 Samba PDC + LDAP setup tutorial at [http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760). My server is 8.04, but the instructions seemed to be almost 100% still applicable. However, when I try to add a Windows XP client to the domain, it gives me an error and the Samba logs have the following messages as well:

```
[2008/12/21 22:39:24, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/12/21 22:39:24, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```

This doesn't make sense, since the LDAP hierarchy is already populated! I've also triple-checked to make sure the config files have the correct passwords as well.

Anyone have any idea how I could debug this? Any direction would be greatly appreciated!

(BTW, I have no idea why Windows is complaining about multiple connections -- I don't have any additional connections open to the server, and I've restarted Samba just to be sure.)

---

### Post by gpredrag on 2008-12-22
It may be that those errors are unrelated.
First error suggests that smbldap-tool haven't created mapping for builtin group Administrators (which is different than Domain Admins), it can be done manually.

Are you sure that there are not any connections  (mapped drives, printers) from windows workstation to the samba server?
Maybe you should try typing:

```
net use \\SAMBA_SERVER_NAME /delete
```
in command prompt on windows computer, before adding computer to the domain.

Also on the samba side,
```
net status sessions
```
would give you sessons on your server.

---

### Post by troyready on 2008-12-23
> **gpredrag said:**
> It may be that those errors are unrelated.
First error suggests that smbldap-tool haven't created mapping for builtin group Administrators (which is different than Domain Admins), it can be done manually.

Are you sure that there are not any connections  (mapped drives, printers) from windows workstation to the samba server?
Maybe you should try typing:

```
net use \\SAMBA_SERVER_NAME /delete
```
in command prompt on windows computer, before adding computer to the domain.

Also on the samba side,
```
net status sessions
```
would give you sessons on your server.

Thanks for the quick reply -- I'm obviously ignorant as to what can be done to fix the lack of mapping for Administrators. I thought I had done it correctly from the guide and have attached a picture of my ldap tree. Please advise as to how I can fix this (or where information is on it)!

As to the existing connections, that did strangely seem to clear up today (must have been something in the cache that expired). But, when I tried again, the following showed up in the log. I imagine this is related to the Administrator mapping problem?

```
[2008/12/22 21:13:58, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/12/22 21:13:58, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
```

---

### Post by gpredrag on 2008-12-23
First of all those group aren't essential for samba (Domain Users, and Domain Admins are, but BUILTIN\Users and BUILTIN\Adminstrators are not), so if everything else works, you are OK.

Seems that samba behavior has changed, and smbldap-tools havent followed all the way, so initial groups creation is not picked up by samba.

There are two interesting parameters for smb.conf that are present in todays samba and I haven't seen them in that howto:

[http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:EDITPOSIX]("http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:EDITPOSIX")
and
[http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:TRUSTED]("http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:TRUSTED")

so if you put:
```

ldapsam:trusted=yes
ldapsam:editposix=yes

```

you can provision samba inital groups with:
```
net sam provision
```
so samba itself creates LDAP entries that it needs.

That's how I populated my LDAP for my second domain, not with smbldap-populate.

For my first domain I wasn't aware of this, and had similar "problems" (again, those groups are not essential for samba, so there were no real problems, it's just that I like my logs clean).
But now, I just can remeber how did I fix it.
It may be that I have put:
ldapsam:trusted=yes
ldapsam:editposix=yes
and just restarted samba,

or run net sam provision afterwards.

Completely different direction would be to add group mappings manually:
[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/groupmapping.html]("http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/groupmapping.html")

---

### Post by troyready on 2008-12-23
> **gpredrag said:**
> First of all those group aren't essential for samba (Domain Users, and Domain Admins are, but BUILTIN\Users and BUILTIN\Adminstrators are not), so if everything else works, you are OK.

Seems that samba behavior has changed, and smbldap-tools havent followed all the way, so initial groups creation is not picked up by samba.

There are two interesting parameters for smb.conf that are present in todays samba and I haven't seen them in that howto:

[http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:EDITPOSIX]("http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:EDITPOSIX")
and
[http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:TRUSTED]("http://us6.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#LDAPSAM:TRUSTED")

so if you put:
```

ldapsam:trusted=yes
ldapsam:editposix=yes

```

you can provision samba inital groups with:
```
net sam provision
```
so samba itself creates LDAP entries that it needs.

That's how I populated my LDAP for my second domain, not with smbldap-populate.

For my first domain I wasn't aware of this, and had similar "problems" (again, those groups are not essential for samba, so there were no real problems, it's just that I like my logs clean).
But now, I just can remeber how did I fix it.
It may be that I have put:
ldapsam:trusted=yes
ldapsam:editposix=yes
and just restarted samba,

or run net sam provision afterwards.

Completely different direction would be to add group mappings manually:
[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/groupmapping.html]("http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/groupmapping.html")

That was very informative -- I think I'm starting to understand now.

I added the lines to smb.conf, and ran "net sam provision", and got the following output:

```
Checking for Domain Users group.
found!
Checking for Domain Admins group.
found!
Check for Administrator account.
Adding the Administrator user.
Unable to allocate a new uid to create the Administrator user!
```

I know I've put in the correct ldap password elsewhere in the binding settings, but reading up on it now it seems I need to set it with "net idmap secret DOMAIN <password>"; unfortunately that results in:

```
The only currently supported backend is LDAP
```

Where have I gone so astray? :confused:

---

