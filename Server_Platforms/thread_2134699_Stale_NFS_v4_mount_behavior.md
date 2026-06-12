---
title: "Stale NFS v4 mount behavior"
date: 2013-04-11
forum: Server Platforms
---

### Post by MakOwner on 2013-04-11
No fix or work around for this?  So we have devolved to windows behavior - reboot if things stop working?

Post Edit: I think this is what's happening to me: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/974374](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/974374)



I have a server that maintains a fairly constant mount from another server using NFS with ver=4 specfied in the mount parameters.

/etc/export from the NFS server (32 bit 12.04 LTS if that makes any difference)
```

/local_export	client_server_name(ro,sync,no_subtree_check)

```

/etc/fstab on client (64 bit 12.04 LTS)
```

server1:/local_export /local/mountpoint nfs ro,vers=4,addr=xxx.xxx.xxx.xxx,clientaddr=xxx.xxx.xxx.xxx

```

I occasionaly take down the Serve side of the NFS link for maintenance - did tonight to replace a failing data disk.

The mountpoint on the client had gone stale -- in NFS v3, that meant a hung mount point as the retries went on .... but as root you could umount -f /local/mountpoint and recover, and remount when it became availble.


Now what I'm seeing is the mount goes stale, the filessystem there goes away and things like 'df' no longer hang waiting on endless retries to complete -- that's great except I can no longer clear and remount.

umount -f /local/mountpoint now returns this:

```

# umount -f /local/mountpoint
/local/mountpoint was not found in /proc/mounts
/local/mountpoint was not found in /proc/mounts
# 

```



attempts to remount it look like this:
```

mount -a
# df
df: `/local/mountpoint': Stale NFS file handle


# mount server1:/local_export /local/mountpoint
mount.nfs: Stale NFS file handle
# 

```

I see the mount in the local /etc/mtab ... How do I clear a stale NFS v4 mount so that I can remount without bouncing the client?

---

