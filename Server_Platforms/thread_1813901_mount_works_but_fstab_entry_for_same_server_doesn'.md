---
title: "mount works but fstab entry for same server doesn't"
date: 2011-07-28
forum: Server Platforms
---

### Post by saphil on 2011-07-28
```
192.168.0.133:/openils   /openils   nfs4 rw,_netdev,auto  0   0 
```
fails to mount the nfs4 share, however
```
# mount -t nfs4 -o proto=tcp,port=2049 192.168.0.133:/openils /openils 
```works just fine

What am I missing?

-Wolf

PS Ubuntu Lucid

---

### Post by arrrghhh on 2011-07-28
> **saphil said:**
> ```
192.168.0.133:/openils   /openils   nfs4 rw,_netdev,auto  0   0 
```
fails to mount the nfs4 share, however
```
# mount -t nfs4 -o proto=tcp,port=2049 192.168.0.133:/openils /openils 
```works just fine

What am I missing?

-Wolf

PS Ubuntu Lucid

Try removing the rw.

```
192.168.0.133:/openils   /openils   nfs4 _netdev,auto  0   0
```

Those permissions are granted on the NFS server, not the client.

If that doesn't work, what's the error you get when you try ```
mount -a
```?

---

### Post by saphil on 2011-07-28
mount -a returns nothing
the reboot will take a minute or 12

==  That worked! Thanks!

---

### Post by skatinjj on 2011-07-28
[https://help.ubuntu.com/community/NFSv4Howto#NFSv4 Client]("https://help.ubuntu.com/community/NFSv4Howto#NFSv4 Client")

Just for reference.

---

### Post by skatinjj on 2011-07-28
Did not see the edit about it working.  Glad it worked.

---

### Post by arrrghhh on 2011-07-28
> **saphil said:**
> mount -a returns nothing
the reboot will take a minute or 12

==  That worked! Thanks!

Didn't need to reboot, mount -a reprocesses /etc/fstab for you ;).  Glad it's workin!  Please use the "Thread Tools" drop-down to mark this thread **[SOLVED]!**

---

### Post by saphil on 2011-07-28
Thanks and thanks again!

---

