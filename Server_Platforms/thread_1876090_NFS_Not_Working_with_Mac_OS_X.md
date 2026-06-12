---
title: "NFS Not Working with Mac OS X"
date: 2011-11-05
forum: Server Platforms
---

### Post by memaster3 on 2011-11-05
The client, which is running Mac OS X 10.7 is not recognizing the files and folders on the nfs mount. Mac OS X says that it is a read only system. Here are the settings on the server and client. The settings for the client NFS Mounts are in disk utility.

[CENTER]SERVER SETTINGS:

Export Folder: [/CENTER]
/jbondhus

[CENTER]Export Folder Owner:[/CENTER]
jon:80 (me and admin group)

[CENTER]Export Folder Permissions:[/CENTER]
-rwxrwxrwx

[CENTER]Export Options:[/CENTER]
/jbondhus       10.0.1.101(rw,sync,no_subtree_check)


[CENTER]CLIENT SETTINGS:

Remote NFS URL[/CENTER]
nfs://10.0.1.100/jbondhus

[CENTER]Mount Location[/CENTER]
/Volumes/test

[CENTER]Advanced Mount Parameters[/CENTER]
None

---

