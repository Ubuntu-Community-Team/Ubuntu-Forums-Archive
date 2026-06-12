---
title: "NFS extremely slow"
date: 2015-03-10
forum: Server Platforms
---

### Post by dave116 on 2015-03-10
I am setting up an NFS server between 2 servers and I keep getting a connection timeout.


Server : 10.10.104.205
Client : 10.10.104.32


From the Server:

Contents of /etc/exports
```

/mnt/storage/share 10.10.104.32(rw,insecure,no_subtree_check,async

```

```

# rpcinfo -p
   program vers proto   port  service
    100000    4   tcp    111  portmapper
    100000    3   tcp    111  portmapper
    100000    2   tcp    111  portmapper
    100000    4   udp    111  portmapper
    100000    3   udp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100227    2   tcp   2049
    100227    3   tcp   2049
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100227    2   udp   2049
    100227    3   udp   2049
    100021    1   udp  49443  nlockmgr
    100021    3   udp  49443  nlockmgr
    100021    4   udp  49443  nlockmgr
    100021    1   tcp  42375  nlockmgr
    100021    3   tcp  42375  nlockmgr
    100021    4   tcp  42375  nlockmgr
    100005    1   udp  44656  mountd
    100005    1   tcp  52783  mountd
    100005    2   udp  48703  mountd
    100005    2   tcp  53390  mountd
    100005    3   udp  50844  mountd
    100005    3   tcp  51961  mountd
    100024    1   udp  55527  status
    100024    1   tcp  56663  status

```

From the NFS Client:

```

# time showmount -e 10.10.104.205

Export list for 10.10.104.205:
/mnt/storage/share 10.10.104.32


real    **2m7.256s**
user    0m0.002s
sys     0m0.006s

```
2 minutes for showmount to return...

```

# mount -v -t nfs 10.10.104.205:/mnt/storage/share /backup/ -overs=3
mount.nfs: timeout set for Tue Mar 10 14:05:11 2015
mount.nfs: trying text-based options 'vers=3,addr=10.10.104.205'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 10.10.104.205 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 10.10.104.205 prog 100005 vers 3 prot UDP port 50844
mount.nfs: mount(2): Connection timed out
mount.nfs: Connection timed out

```

```

# mount -v -t nfs 10.10.104.205:/mnt/storage/cpanel/cp06.domains.co.za /backup/
mount.nfs: timeout set for Tue Mar 10 14:22:31 2015
mount.nfs: trying text-based options 'vers=4,addr=10.10.104.205,clientaddr=10.10.104.32'
mount.nfs: mount(2): Connection timed out
mount.nfs: Connection timed out



```


```

# nc -zv 10.10.104.205 111
Connection to 10.10.104.205 111 port [tcp/sunrpc] succeeded!

```



iptables is disabled on both client and server, so I can rule out firewall.

Any ideas?

---

### Post by SeijiSensei on 2015-03-10
I know this sounds trivial, but is the closing parenthesis in the options list in /etc/exports really missing?  What if you add it?

---

### Post by dave116 on 2015-03-10
Managed to get it sorted.

It was the HP Procurve 1810 switch - under the security settings it has "Storm Control" and "Anti-DDos" enabled by default.
It seems to be blocking NFS packets.

[SOLVED]

---

