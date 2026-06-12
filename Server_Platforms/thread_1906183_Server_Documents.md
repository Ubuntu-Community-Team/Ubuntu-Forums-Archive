---
title: "Server Documents"
date: 2012-01-08
forum: Server Platforms
---

### Post by kr651129 on 2012-01-08
I have a Ubuntu 11.10 x32 server running a samba share, I'd like my documents, pictures, and music folder to point to these folders on the server by default, is there any easy way to do this?

---

### Post by Buntumatic on 2012-01-08
No problem, I'd share those directories via NFS as well and use symlinks.

---

### Post by SeijiSensei on 2012-01-09
> **kr651129 said:**
> I have a Ubuntu 11.10 x32 server running a samba share, I'd like my documents, pictures, and music folder to point to these folders on the server by default, is there any easy way to do this?

On which machine?  The client?  A Windows client or a Linux client?  

For Windows clients, I'd recommend using the "map a network drive" option to assign a drive letter to the remote share.  Then use Windows shortcuts to link the Documents, etc., directories on the remote share to your Windows home directory.

If you're using a Linux client, the NFS+symlinks option Buntumatic recommends is the best choice.

---

