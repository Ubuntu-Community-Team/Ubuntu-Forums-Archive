---
title: "MoinMoin access configuration"
date: 2008-08-10
forum: Server Platforms
---

### Post by sebald on 2008-08-10
Have just done a trial install of MoinMoin according to the Ubuntu Server (8.04 LTS) guide. Only problem is that access control according to the built-in documentation doesn't seem to work.
I've set up farmconfig.py with:
```
#acl_rights_before = u"UserName:read,write,delete,revert,admin"
```
and declared myself superuser:
```
#superuser = u"UserName"
```
and restarted Apache, etc., no dice, everything still wide open. Can't do it on a per-page basis, if I put this in the page header:
```
#acl SomeUser:read,write All:read
```
it says "You can't change ACLs on this page since you have no admin rights on it!" (that's even when logged in)
I read HelpOnAccessControl, tried putting global commands in the mywiki.py file, restarting Apache, etc., still wide open.
Am I putting things in the wrong place or what?

---

