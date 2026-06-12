---
title: "Question about permissions for a mounted samba share"
date: 2010-01-09
forum: Server Platforms
---

### Post by Harry Muscle on 2010-01-09
I have one linux machine (we'll call it the server) that shares out a few Samba shares.  The folders and files on these shares are for the most part  permissioned for read write access by only USER1 (UID:1002) and GROUP1 (GID:1001).  On my second linux machine where I'm mounting these shares, there is no user or group that matches the UID or GID, so the  permissions show only the UID and GID for the user and group that have access.  Since the permissions don't allow Others any access I can't access any files on these mounted shares.

I log into the second machine also with USER1 but the UID is 1000, so would the correct way to fix this problem be to change USER1 on the second machine to have a UID of 1002 (to match the UID on the server) and create a group with a UID of 1001 to match the group and GID on the server?  Or is there another way to correct this problem?

The end outcome I want to have is that USER1 on the second machine gets whatever permissions USER1 on the server had for the files on the share I'm trying to mount.

Thanks,
Harry

---

