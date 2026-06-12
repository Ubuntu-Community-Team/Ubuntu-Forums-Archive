---
title: "Samba4: How to Edit sam.ldb"
date: 2013-12-13
forum: Server Platforms
---

### Post by lingpanda on 2013-12-13
So the wiki [https://wiki.samba.org/index.php/Samba4/LDBIntro](https://wiki.samba.org/index.php/Samba4/LDBIntro) has this for the syntax: username@computername:~/Samba/samba-master$ bin/ldbedit -e vim -H st/dc/private/sam.ldb '(samaccountname=guest)'. However I do not follow. Specifcally this "st/dc/". If I attempt to point to my location of sam.ldb it says file not found. Has anyone successfully used ldbedit? Thanks.

---

### Post by karzak on 2014-04-26
try locate try *locate sam.ldb* then [I]ldbedit -e vim -H <returned path>/sam.ldb '(samaccountname=guest)'

[/I]Sorry for the bump and post necromancy! But it might help someone else...

[COLOR=#000000][/COLOR]

---

