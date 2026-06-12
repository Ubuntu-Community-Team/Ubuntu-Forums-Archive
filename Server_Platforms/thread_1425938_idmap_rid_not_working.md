---
title: "idmap rid not working"
date: 2010-03-09
forum: Server Platforms
---

### Post by necrolyte2 on 2010-03-09
I have 2 servers running 9.10(Samba 3.4) and I need both of them to use the same uid/gid mappings in Samba.

It seems that idmap_rid is what I want to use, however, I cannot seem to get it to work. I've searched pretty much everywhere and cannot find anything.

When I issue wbinfo -i <domain user> it returns 
```
username:*:501:505:username:/home/ourworkgroup/username:/bin/bash
```

Both servers are joined to an AD domain and that seems to be working just fine as it actually looks up the users in AD and returns their sid, it just doesn't seem to be doing the actual sid -> uid mapping

which seems like it should be returning the uid in the range that I specify in the smb.conf file

smb.conf file
```
[GLOBAL]
	realm = our.realm.name
	workgroup = ourworkgroup
	security = ads
	password server = our.password.server
	idmap uid = 10000-20000
	idmap gid = 10000-20000
	idmap config ourworkgroup : backend = rid
	idmap config ourworkgroup : range = 10000-20000
	idmap config ourworkgroup : default = yes
	idmap config ourworkgroup : base_rid = 0
	idmap backend = rid
	allow trusted domains = no
	template shell = /bin/bash
	template homedir = /home/%D/%U
	winbind use default domain = yes
	log level = 3
```

I've changed the realm and workgroup names just to mask them

I've tried all different forms of formatting the idmap options to use rid including
```
idmap backend = rid:ourworkgroup=10000-20000
```

with still no luck

I'm sure I'm forgetting to post more info so please feel free to ask for it.

---

