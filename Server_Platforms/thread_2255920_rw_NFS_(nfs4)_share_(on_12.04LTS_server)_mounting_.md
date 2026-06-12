---
title: "rw NFS (nfs4) share (on 12.04LTS server) mounting as ro on client (10.04LTS)"
date: 2014-12-08
forum: Server Platforms
---

### Post by Doug_Miller on 2014-12-08
I'm trying to set up an NFS share between two servers on the same subnet. I've got to the point where the mount is succeednig on the client, but that mount is readonly.

I'm assuming it likely has something to do with /etc/exports, but I'm not 100% sure. This is what I have there:
```

/home           {clientIP}(rw,async,nohide,insecure,no_root_squash,no_subtree_check)
/var/nfs        {clientIP}(rw,async,nohide,insecure,no_subtree_check)

```

/home has root:root permissions. /var/nfs has nobody:nogroup permissions.

Am I doing something wrong with the /etc/exports configuration, permissions, or possibly something else? The response to a mount on the client is this:
```

{serverIP}:/var/nfs on /mnt/nfs/var/nfs type nfs4 (ro)

```

Thanks for any and all help!

---

