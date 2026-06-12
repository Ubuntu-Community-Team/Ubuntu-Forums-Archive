---
title: "permission issues with kerberized nfs4"
date: 2012-03-23
forum: Server Platforms
---

### Post by domgross on 2012-03-23
While this is not strictly related to ubuntu server edition I figured this might a good place to ask for some insight on the following problem.

I am running a debian (squeeze) server with diskless ubuntu (lucid, precise) clients. User home directories are exported from the server via kerberized nfs4, the root file system for the diskless clients is exported via nfs3. 

This works fine, however when I try to mount the diskless root filesystem as user root things go awry. To start from the beginning:

/etc/exports:
```

/nfs3/rootfs    192.168.1.0/24(fsid=1,ro,no_subtree_check,sync,no_root_squash)


/nfs4           192.168.1.0/24(sec=krb5i:krb5p,fsid=2,rw,secure,no_subtree_check,sync,no_root_squash,crossmnt)
/nfs4/home      192.168.1.0/24(sec=krb5i:krb5p,fsid=3,rw,secure,no_subtree_check,sync,no_root_squash)
/nfs4/rootfs    192.168.1.0/24(sec=krb5i:krb5p,fsid=4,rw,secure,no_subtree_check,sync,no_root_squash)

```

/nfs3/rootfs and /nfs4/rootfs are mapped to the same directory. For what it is worth setting the /nfs3/rootfs export to rw here does not make a difference.

There exists a principal [email]root@FOO.BAR[/email] and idmap on the server is working correctly:

```
rpc.idmapd[28536]:  Server: (group) id "0" -> name "root@FOO.BAR"
rpc.idmapd[28600]:  Server: (user) id "0" -> name "root@FOO.BAR"

```

also on the client:

```

rpc.idmapd: Client 6: (user) name "root@FOO.BAR" -> id "0"
[snip]
rpc.idmapd: Client 6: (group) name "root@FOO.BAR" -> id "0"

```


Signing in as [email]root@FOO.BAR[/email]:
```

root@client  kdestroy
root@client  kinit -p root
root@client  klist

Ticket cache: FILE:/tmp/krb5cc_10098_vz3476
Default principal: root@FOO.BAR

Valid starting       Expires              Service principal
23.03.2012 22:00:47  24.03.2012 08:00:47  krbtgt/FOO.BAR@FOO.BAR
        renew until 24.03.2012 22:00:44

```

mount /nfs4/rootfs:```

root@client   mount -vvvt nfs4 -o sec=krb5i,nolock,rw server:/rootfs tmp
mount: fstab path: "/etc/fstab"
mount: mtab path:  "/etc/mtab"
mount: lock path:  "/etc/mtab~"
mount: temp path:  "/etc/mtab.tmp"
mount: UID:        0
mount: eUID:       0
mount: spec:  "server:/rootfs"
mount: node:  "tmp/"
mount: types: "nfs4"
mount: opts:  "sec=krb5i,nolock,rw"
mount: external mount: argv[0] = "/sbin/mount.nfs4"
mount: external mount: argv[1] = "server:/rootfs"
mount: external mount: argv[2] = "tmp/"
mount: external mount: argv[3] = "-v"
mount: external mount: argv[4] = "-o"
mount: external mount: argv[5] = "rw,sec=krb5i,nolock"
mount.nfs4: timeout set for Fri Mar 23 22:07:12 2012
mount.nfs4: trying text-based options 'sec=krb5i,nolock,addr=serverip,clientaddr=clientip'
server:/rootfs on /tmp type nfs4 (rw,sec=krb5i,nolock)
```

So far so good, but I can't access files which can only be access by root. Trying to read:
```

root@server ls -aln /rootfs/etc/shad*
-rw-r----- 1 0 0 1354 Mar 22 09:51 /rootfs/etc/shadow
```


results in:
```

root@client    less tmp/etc/shadow
tmp/etc/shadow: Permission denied
```


nothing else sticks out in the log files (kern.log, syslog) on either the server or the client, except this

```

server kernel: [4779793.976031] RPC: AUTH_GSS upcall timed out.
server kernel: [4779793.976033] Please check user daemon is running.
```

which seems to be unrelated: [http://www.itp.uzh.ch/~dpotter/howto/kerberos]("http://www.itp.uzh.ch/~dpotter/howto/kerberos").

What am I missing? I only have basic knowledge of the whole kerberos / nfs business, so any ideas on which other logs to look at / how to get more debug information or a better understanding of what is going on is much appreciated.

---

### Post by domgross on 2012-03-26
Turns out this is by design:

[http://linux-nfs.org/pipermail/nfsv4/2005-August/002431.html](http://linux-nfs.org/pipermail/nfsv4/2005-August/002431.html)

> 
Currently when using kerberos, all accesses by root use the client  machine's machine credentials ('nfs/[hostname at REALM]("http://linux-nfs.org/cgi-bin/mailman/listinfo/nfsv4")').  [Yes, there are  plans to change that.]  Unless you have a mapping for 'nfs/hostname' on  the server, it will be mapped to nobody.Solution can be found here:
[http://comments.gmane.org/gmane.linux.nfsv4/6126](http://comments.gmane.org/gmane.linux.nfsv4/6126)

So when using nsswitch as translation method in idmapd nfs/hostname@REALM has to be mapped to the user root in the static section of idmapd.conf.

---

