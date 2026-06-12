---
title: "OpenLDAP or similar to slave from Windows AD"
date: 2014-11-27
forum: Server Platforms
---

### Post by Jonathan L on 2014-11-27
Hi All

It has been a long time since I've done any integration with Windows, and never Active Directory, but now a client requirement is approximately like this:

* Client is approx 50 users on a single site
* A single Windows Active Directory system (believed to be Windows 2012) at Site 1
* Solving a disaster recovery requirement for very simple, minimal subset, business-critical services at Site 2
* We want to do offline verification of users, on an Ubuntu server, at the DR site

My proposed route was to extract the user names, hashed passwords, and user full names with ldapsearch running on a new Ubuntu server at Site 1, then rynsc/scp/whatever over encrypted link to Ubuntu server at Site 2; which then validates users against the username/hash in the file.  Run the updater hourly/daily/whatever by cron.

I can run programs on the Windows server if necessary, run anything reasonable on the adjacent Ubuntu server at Site 1.  What I can't do is have incoming live requests from Site 2 (it's for disaster recovery!), run any Windows at Site 2, or change much on the Windows server (no password interceptors, for example).

Many ldapsearch examples show base64-encoded hashed password: though it seems *not* from a Windows Active Directory server.  Using [Active Directory Explorer]("http://en.wikipedia.org/wiki/Active_Directory_Explorer") shows no passwords in any form I can see.

My ldapsearch is working properly (on Ubuntu server at Site 1):
```
$ ldapsearch -vv -H ldap://192.168.0.1 -D "ad@mydomain.com" -w 'secret' -b "dc=mydomain,dc=com" sAMAccountName=hst givenName cn userPassword
...
dn: CN=Hunter S. Thompson,CN=Users,DC=mydomain,DC=com
cn: Hunter S. Thompson
givenName: Hunter
```

It's clear we can get the hashes as the [fgdump]("http://foofus.net/goons/fizzgig/fgdump/") tool reports them (this is over RDP on Windows server):
```

hst:1105:NO PASSWORD*********************:59BC79163E3EAD6F5657A3DE87ADF398:::

```which is easy to verify against:```

php -r 'echo hash("md4", iconv("UTF-8", "UTF-16LE", "fearandloathing1."));'

```

As it stands this would satisfy the goals but it's frankly shameful, and fgdump is going to take a bit of explaining to the security team!

Am I barking up the wrong tree?  Do I have to make some kind of trust and sync the AD to OpenLDAP on the Ubu server at site 1?  Do I have to tickle some internal setting the Windows AD server?

Many thanks for any suggestions.

Jonathan

---

