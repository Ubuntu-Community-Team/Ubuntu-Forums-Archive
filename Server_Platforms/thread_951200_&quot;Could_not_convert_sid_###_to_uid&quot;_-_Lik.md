---
title: "&quot;Could not convert sid ### to uid&quot; - Likewise-Open"
date: 2008-10-17
forum: Server Platforms
---

### Post by kpm on 2008-10-17
Hi, I am using the following [PDF how-to]("http://www.likewisesoftware.com/resources/user_documentation/Likewise-Samba-Guide.pdf") from Likewise.  This how-to is for Likewise Enterprise, not Likewise-Open, so there are some changes to required (there is no /usr/centeris/ directory or 'lwicompat_v2.so' and 'lwicompat_v4.so' files).  I learned this from this [ubuntu forum post]("http://ubuntuforums.org/showpost.php?p=5399487&postcount=15") but the poster seems to have got this working.
I have a Ubuntu 8.04 LAMP server that I would like anyone in the Windows Active Directory domain-admin security group to be able to browse to shares with Window's Explorer.

Just near the end of the how to, the instructions state:

> $ wbinfo -t
checking the trust secret via RPC calls succeeded
3. Next resolve a name to a SID and that SID to a uid or gid. This example resolves the user EAST\testuser1001:
$ wbinfo -n "EAST\testuser1001"
S-1-5-21-1862414975-1169984241-1344135624-1103 User (1)
$ wbinfo -S S-1-5-21-1862414975-1169984241-1344135624-1103
200000
This should match the information returned from getent which is
sent through Likewise Authentication daemon.
$ getent passwd "EAST\testuser1001"
EAST\testuser1001:*:200000:200000::/home/EAST/testuser1001:/bin/bash  

The step that requests 'wbinfo -S ...' is where I encounter the error "Could not convert sid S-1-5-21-etc to uid"

Can anyone point me to what may be causing this??

Thanks

ps I tried to add this post to the one posted above but when I attempt to, I get an error telling me I don't have permission to...

---

### Post by dsscheib on 2008-11-05
try using wbinfo -s rather than wbinfo -S

---

### Post by dsscheib on 2008-11-05
Ignore my previous response. I see what you're trying to do now. I'll reply if I figure out why it is failing.

---

### Post by likeWiseGuy on 2008-11-10
> **kpm said:**
> Hi, I am using the following [PDF how-to]("http://www.likewisesoftware.com/resources/user_documentation/Likewise-Samba-Guide.pdf") from Likewise.  This how-to is for Likewise Enterprise, not Likewise-Open, so there are some changes to required (there is no /usr/centeris/ directory or 'lwicompat_v2.so' and 'lwicompat_v4.so' files).  I learned this from this [ubuntu forum post]("http://ubuntuforums.org/showpost.php?p=5399487&postcount=15") but the poster seems to have got this working.
I have a Ubuntu 8.04 LAMP server that I would like anyone in the Windows Active Directory domain-admin security group to be able to browse to shares with Window's Explorer.

Just near the end of the how to, the instructions state:

 

The step that requests 'wbinfo -S ...' is where I encounter the error "Could not convert sid S-1-5-21-etc to uid"

Can anyone point me to what may be causing this??

Thanks

ps I tried to add this post to the one posted above but when I attempt to, I get an error telling me I don't have permission to...

Hi, kpm.

Can you please give me more information on your domain environment? How many domain controllers are you running? How many domains are in your environment? When you cannot resolve the SID to UID, can you at least log into that system with a domain account?

I'll do my best to work with you to get this resolved.

Thanks.

---

### Post by larslj on 2008-11-12
Hi, I'm experiencing the exact same problem here. I can log in with SSH using my domain account but I'm having trouble getting it to work with Samba.

Files created from Windows are owned by <username>/domain^users on the Linux side. But when browsing the server from Windows the owner is S-1-0-0. I get access denied when trying to change the access rights.

I think we are running 2 domain controllers for one single domain, but there are a bunch of foreign domains as well (I don't know much about AD and stuff so I might use the wrong vocabulary).

---

### Post by Sergiodf on 2008-12-30
> **kpm said:**
> 
The step that requests 'wbinfo -S ...' is where I encounter the error "Could not convert sid S-1-5-21-etc to uid"

kpm, did you solve this? I have the same problem and can't figure it out.

I can log by ssh with a domain account.
I can do `wbinfo -t`.
`net ads testjoin` is ok.
`lwiinfo -S S-1-...` works but `wbinfo -S S-1-...` not. :confused:

---

### Post by Sergiodf on 2008-12-30
> **Sergiodf said:**
> `lwiinfo -S S-1-...` works but `wbinfo -S S-1-...` not. :confused:

Running winbind in console (`/usr/sbin/winbind -SFi -d3`) show an error when i do `wbinfo -S S-1-...`:
```
[...]
Successfully added idmap alloc backend 'ldap'
Successfully added idmap backend 'ldap'
Successfully added idmap alloc backend 'tdb'
Successfully added idmap backend 'tdb'
Successfully added idmap backend 'passdb'
Successfully added idmap backend 'nss'
Initializing idmap domains
Probing module 'lwopen'
Probing module 'lwopen': Trying to load from /usr/lib/samba/idmap/lwopen.so
Module '/usr/lib/samba/idmap/lwopen.so' loaded
Successfully added idmap backend 'lwopen'
smb_register_idmap_nss: Successfully added idmap nss backend 'lwopen'
Forcing to readonly, as this module can't store arbitrary mappings.
[COLOR="Red"]/usr/sbin/winbindd: symbol lookup error: /usr/lib/samba/idmap/lwopen.so: undefined symbol: wcache_tdc_fetch_list[/COLOR]
Added timed event "async_request_timeout": 901bc0
timed_events_timeout: 299/999501
Destroying timed event 901bc0 "async_request_timeout"
Could not receive async reply from child pid 12240
Could not trigger sid2uid
Could not convert sid S-1-5-21-1334982723-1816155474-3506049719-1120
```
Obviously it doesn't happen on likewise-winbind executing `lwiinfo -S S-1-...`:
```
[...]
Successfully added idmap alloc backend 'ldap'
Successfully added idmap backend 'ldap'
Successfully added idmap alloc backend 'tdb'
Successfully added idmap backend 'tdb'
Successfully added idmap backend 'passdb'
Successfully added idmap backend 'nss'
Initializing idmap domains
Probing module 'lwopen'
Probing module 'lwopen': Trying to load from /usr/lib/likewise-open/idmap/lwopen.so
Module '/usr/lib/likewise-open/idmap/lwopen.so' loaded
Successfully added idmap backend 'lwopen'
smb_register_idmap_nss: Successfully added idmap nss backend 'lwopen'
Forcing to readonly, as this module can't store arbitrary mappings.
lwopen:be_init() Adding WEBAPPS (S-1-5-21-1660839927-3497730885-1109396497) -> 1269
lwopen:be_init() Adding INFOIL (S-1-5-21-1334982723-1816155474-3506049719) -> 2135
Domain default - Backend lwopen - default - readonly
Domain WEBAPPS - Backend passdb - not default - readonly
Initializing idmap alloc module
Opening tdbfile /var/lib/samba/winbindd_idmap.tdb
Returning valid cache entry: key = IDMAP/SID/S-1-5-21-1334982723-1816155474-3506049719-1120, value = IDMAP/UID/1119356000, timeout = Tue Dec 30 16:26:35 2008
Storing response for pid 12312, len 3496
Destroying timed event 7f34b6573bf0 "async_request_timeout"
Retrieving response for pid 12312
```
I think is a package problem. It seems like lwopen.so is calling a function defined in likewise-winbind but not in samba's one. =o(
Maybe a package is out of date? I'm using:
-winbind 3.0.28a-1ubuntu4.7
-likewise-open 4.0.5-0ubuntu3.1

# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

---

### Post by kpm on 2009-01-04
> **Sergiodf said:**
> kpm, did you solve this? I have the same problem and can't figure it out.

I can log by ssh with a domain account.
I can do `wbinfo -t`.
`net ads testjoin` is ok.
`lwiinfo -S S-1-...` works but `wbinfo -S S-1-...` not. :confused:

Sorry for delayed response.. I lost track of this issue as I had to move onto a different project... Never did resolve... accomplished the basics of what we needed with a simple samba share and moved.

---

### Post by johanan on 2009-03-02
I am having the exact same problem. 
lwiinfo -S returns a value, but wbinfo -S throws the "Could not convert sid S-1-5-21-etc to uid" error.

I am running Ubuntu Server 8.04 64 bit. I have installed Likewise-open from the repository and I can login as a domain user. I followed the instructions at [http://chrplunk.blogspot.com/2008/06/allow-windows-clients-in-active.html](http://chrplunk.blogspot.com/2008/06/allow-windows-clients-in-active.html) in one of the comments. I also think that the instructions are also on the forums somewhere.

In the winbind log I found the same error: 

/usr/sbin/winbindd: symbol lookup error: /usr/lib/samba/idmap/lwopen.so: undefined symbol: wcache_tdc_fetch_list

I am going to try a fresh install of 32 bit and see if I can repeat the problem.

This is currently a test server and if I can get this to work I would be able to switch at least 3 of our servers off of Windows 2003 and to Ubuntu.

---

### Post by johanan on 2009-03-02
This works fine in 32 bit.

---

### Post by Vantrax on 2009-03-03
Please create a bug report if you have not already.

---

### Post by Sergiodf on 2009-03-03
:arrow: [https://bugs.launchpad.net/bugs/337203](https://bugs.launchpad.net/bugs/337203)

---

### Post by Sergiodf on 2009-03-20
> **Sergiodf said:**
> :arrow: [https://bugs.launchpad.net/bugs/337203](https://bugs.launchpad.net/bugs/337203)
The bug have been marked as invalid. It seems that we follow an inappropriate howto.

Maybe we shouild forget LikeWise completely and use plain samba: :arrow: [https://help.ubuntu.com/community/SettingUpSamba#Active%20Directory%20Integrated%20File%20Server](https://help.ubuntu.com/community/SettingUpSamba#Active%20Directory%20Integrated%20File%20Server).
I don't know if Ubuntu documentation still applies (it says is written based on 6.06/6.10) and i will not verify it (our server will be migrated to Windows 2003 next month, not my decision).

Good luck.

---

