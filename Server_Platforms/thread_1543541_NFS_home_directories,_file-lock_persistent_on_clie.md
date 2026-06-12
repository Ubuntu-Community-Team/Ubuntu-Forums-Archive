---
title: "NFS home directories, file-lock persistent on client reboot"
date: 2010-08-01
forum: Server Platforms
---

### Post by abuster on 2010-08-01
Hi!

Googled and searched the forum a lot, and can't seem to find a good answer to this problem.

I have a NFS fileserver, exporting home directories. Upon client reboot, file-locks don't seem to get flushed. When client boots up again, it complains about not being able to update .ICEauthority.

If I reboot the fileserver, it seems like file-locks are flushed, as clients can boot up without warning about .ICEauthority.


[B][SIZE=2]Server (Ubuntu 10.04 lucid lynx)
[/SIZE][/B]/etc/exports:
```
/home  10.255.254.0/24(rw,sync,no_subtree_check)
```Populate passwd, group and shadow on clients with scp.

Worth to mention is that /home is a zfs. Using zfs-fuse version 0.6.9 in ppa listed on zfs-fuse.net
zpool status:
```

  pool: home
 state: ONLINE
 scrub: none requested
config:

    NAME        STATE     READ WRITE CKSUM
    home        ONLINE       0     0     0
      raidz1-0  ONLINE       0     0     0
        sdb     ONLINE       0     0     0
        sdc     ONLINE       0     0     0
        sdd     ONLINE       0     0     0

```**[SIZE=2]Clients (Linux Mint 9)[/SIZE]**
/etc/fstab:
```
filserver.lan:/home /home    nfs    _netdev,auto    0    0
```Portmap is not bound to localhost on either server or client.

I know that it's possible to use another location for .ICEauthority, like /tmp. But this does not feel like a good solution, as you could get the same problem on other files. 

And if using another location for .ICEauthority is the only foolproof solution, where should one config this on Linux Mint 9/Ubuntu 10.04?

Any push in right direction is greatly appreciated! :)

---

### Post by abuster on 2010-08-06
Found this on .ICEathority:
[http://ubuntuforums.org/showthread.php?t=26005](http://ubuntuforums.org/showthread.php?t=26005)

---

### Post by abuster on 2010-10-06
Found this in "man nfs":

```
lock / nolock  Selects whether to use the NLM sideband protocol to lock
                      files on the server.  If neither option is specified (or
                      if lock is specified), NLM  locking  is  used  for  this
                      mount point.  When using the nolock option, applications
                      can lock files, but such locks  provide  exclusion  only
                      against  other  applications running on the same client.
                      Remote applications are not affected by these locks.

                      NLM locking must be disabled with the nolock option when
                      using NFS to mount /var because /var contains files used
                      by the NLM implementation on Linux.   Using  the  nolock
                      option  is  also  required  when mounting exports on NFS
                      servers that do not support the NLM protocol.
```

And in /usr/share/doc/zfs-fuse/STATUS:
```
What isn't working yet (expected version):

- Mount options (0.6.0).
- File locks (0.6.0).

```

Seems like file locks aren't supported i ZFS yet. Haven't tried "nolock" though, made .ICEathority save to /tmp.

Also made automatic user login wait 3 seconds, to have file system settle down. Seems like the computer boots to quick to get up both network and NFS.

---

