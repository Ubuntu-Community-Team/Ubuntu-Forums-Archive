---
title: "System user is ignoring group permissions on an nfs4 mount"
date: 2010-10-27
forum: Server Platforms
---

### Post by Brazen on 2010-10-27
I've created a user like this on both computers (the nfs server and the nfs client)

```
sudo adduser --system --group --no-create-home myuser
```

I set the exported directory to be owned by myuser.myuser (both the user and the group) and gave it 770 permissions.  I mount the export on the client at /mnt/nfs4dir, change the myuser shell to /bin/bash, and su to myuser.

Now as myuser on the client, I can not access /mnt/nfs4dir.  I can not access an nfs mount from a directory that is owned by this system user and this user's group.

id mapping working fine.  The user and group ownership show up correctly on the client.  I can even create another user without the --system option and add that user to the myuser group, then that new user can access /mnt/nfs4dir even though myuser can't.  I can even chmod the dir to 777 and then myuser can access, but that's not a viable option.

So the user seems to be ignoring the group and user ownership of an nfs mounted directory.  But this is only a problem for a system user and doesn't affect regular users.  Any ideas why?  and how to fix?

---

