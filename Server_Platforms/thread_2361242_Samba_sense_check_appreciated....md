---
title: "Samba sense check appreciated..."
date: 2017-05-14
forum: Server Platforms
---

### Post by KillerKelvUK on 2017-05-14
TL;DR

Is my reading correct that Unix Extensions are not support when clients are using SMBv2 or greater to connect to the server?  And if so is this where the 'uid' and 'gid' mount options help provide the file ownership details that were previously negotiated using unix extensions in NT1/SMBv1?


Long version...

Decided to look at samba in more detail and noted my clients all connected using NT1 and wanted to change this to v2/3 for speed and security.  Easy enough and client mounts succeed but I've now noticed the clients mount the share as root/root whereas under NT1/SMBv1 the permissions for the share on the server would map across to the clients provided the uid's and gid's existed and matched, I also noted the client mount options for NT1 vs SMBv2/3 altered from unix to nounix.  I run 17.04 on my server and everything is updated from the stock sources so my samba server package is currently v4.5.8, I've never really looked into samba previous as my requirements are lightweight so would just appreciate a sense check of my reading so far to ensure I'm not going Alice in Wonderland.

Thanks.

---

### Post by bab1 on 2017-05-15
You are correct.  This is because UNIX extensions have not yet been defined for the SMB2 or SMB3.

---

### Post by KillerKelvUK on 2017-05-15
Thank you @bab1

---

