---
title: "One fileserver for multiple servers to access"
date: 2009-02-06
forum: Server Platforms
---

### Post by samosamo on 2009-02-06
In one server closet, we will have five application servers plus another file server which acts as a central data location. I'm having trouble visualizing this network setup. How would this be deployed in a production environment, considering security and performance?

These are all linux machines so I figure NFS is the choice of service but unfortunately I do not have much experience with it. Is there any security protocol for this purpose or should I just treat the servers as users on LDAP?  Would all the uid/gid's have to match on each system? These are all guesses at this point.

So this is the most simple method I can come up with. Not really considered security, but just a little "organization" if you will. An /etc/exports would appear as the following:

```
fileserver:~/$ cat /etc/exports
/srv/nfs/machine101 10.0.0.101(rw)
/srv/nfs/machine102 10.0.0.102(rw)
/srv/nfs/machine103 10.0.0.103(rw)
...
``` ... and so on, which secures it via IP.

---

### Post by samosamo on 2009-02-06
bump, I could use some help with this.

---

### Post by samosamo on 2009-02-13
ttt

---

### Post by HermanAB on 2009-02-14
Howdy,

You are on the right track - just keep going!

NFS is very easy to set up.  It requires only one line on the server in /etc/export and one line in /etc/fstab on each client.  Google for examples.

If you don't use NIS, then all user UIDs and GIDs have to match.

Cheers,

Herman

---

