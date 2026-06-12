---
title: "NFS share to Mac revisited"
date: 2012-02-02
forum: Server Platforms
---

### Post by sebrock on 2012-02-02
So my NFS shares have been working fine until recently. I have no idea why it has suddenly stopped. I can mount and read everything but writing is gone.

From my ubuntu server (10.04) this is the /etc/exports:

```
/var/Files/500GB                        192.168.0.0/24(rw,async,insecure,no_subtree_check,all_squash,anonuid=1000,anongid=1000)
/var/Files/200GB                        192.168.0.0/24(rw,async,insecure,no_subtree_check,all_squash,anonuid=1000,anongid=1000)
```

As you probably know the UID of the mac user is 501. Now all_squash and anonuid=1000 should set permissions to default to the ubuntu server user. But somehow it seems not to.

Any suggestions? :confused:

---

### Post by rubylaser on 2012-02-02
This works fine to our Snow Leopard and Lion clients at the office from our Ubuntu 10.04 server.

```
/var/marketing  10.1.1.0/24(rw,async,insecure,no_subtree_check)
```

---

