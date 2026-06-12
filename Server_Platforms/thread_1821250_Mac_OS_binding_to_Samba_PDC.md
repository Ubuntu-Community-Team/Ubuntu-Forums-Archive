---
title: "Mac OS binding to Samba PDC"
date: 2011-08-08
forum: Server Platforms
---

### Post by yujin1st on 2011-08-08
Hello.

Does anyone join a Mac OS to Samba PDC?

My point is to build a single domain for different clients (win xp, win 7, mac os 10.6) with home folders and roaming profiles.

I see 2 posible solutions:
1. Win binds to Samba PDC, Mac binds to OpenLDAP. In this case, OpenLDAP requires some schemas (see down this topic). And i don't know how to manage this.
2. All clients bind to Samba Domain. Mac client thinks it join to AD, and doesn't need something else. As i found, mac requires Kerberos. 

I've installed Ubuntu Server 10.04 + OpenLDAP + Samba PDC + Gosa (for managment). It works fine with windows clients, but macintosh machines don't want to bind for some reasons:
1. Binding to OpenLDAD. It requires some apple schemes. When i try to add converted schemas from mac os  (/etc/openldap/schema/apple.schema) it says i haven't necessary objectClasses. As i understood it needs apple samba schema, but i have already installed own schemes.
2. Binding to Samba PDC as AD 
It requires Kerberos. In this case i don't know what should i do? How should i install it: as a backend for samba, where should i hold principal base, etc...?

ps: Own mac os x 10.6 server  works fine with mac clients through Open Directory (OpenLDAP variant). But win clients with Samba don't work for some reasons...

---

