---
title: "Targetcli ISCSI cannot create portals"
date: 2016-09-09
forum: Server Platforms
---

### Post by duncan831 on 2016-09-09
**I am trying to create an ISCSI target. But i cannot create a portal. Default portal will not be created:***/iscsi> create iqn.2016-04.world.srv:storage.target00
Created target iqn.2016-04.world.srv:storage.target00.
Created TPG 1.
Default portal not created, TPGs within a target cannot share ip:port.
/iscsi> ls
o- iscsi .......................................................... [Targets: 1]
o- iqn.2016-04.world.srv:storage.target00 .......................... [TPGs: 1]
o- tpg1 ............................................. [no-gen-acls, no-auth]

  o- acls ........................................................ [ACLs: 0]

  o- luns ........................................................ [LUNs: 0]

  o- portals .................................................. [Portals: 0]
/iscsi>*
**After that i tried to create it manually:**
/iscsi/iqn.20.../tpg1/portals> create
Using default IP port 3260
Binding to INADDR_ANY (0.0.0.0)
Could not create NetworkPortal in configFS

**Please help me out :)**

---

### Post by darkod on 2016-09-09
Can something like this help you: [https://linhost.info/2012/05/configure-ubuntu-to-serve-as-an-iscsi-target/](https://linhost.info/2012/05/configure-ubuntu-to-serve-as-an-iscsi-target/)

It doesn't mention you need to create a portal, it might be done automatically. Also you don't need to work from iscsi command line, you can do it from the standard command line.

---

### Post by duncan831 on 2016-09-09
Default portal is not created with targetcli. 

Ill try your link soon.

---

### Post by duncan831 on 2016-09-09
Default portal is not created with targetcli. 

Ill try your link soon.

---

### Post by duncan831 on 2016-09-27
Ive tried the link. 

I Was able to setup. Original post did go wrong because of already configured ISCSI with iscsi-target.

---

