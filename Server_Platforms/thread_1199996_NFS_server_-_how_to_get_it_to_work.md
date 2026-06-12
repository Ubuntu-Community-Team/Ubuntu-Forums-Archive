---
title: "NFS server - how to get it to work?"
date: 2009-06-29
forum: Server Platforms
---

### Post by zong1 on 2009-06-29
Hi there, 

  Quick question about debugging my NFS server:

/etc/exports:
/home/my/Desktop/HOME-NETWORK 192.168.1.200(ro,no_root_squash)

# rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  45941  status
    100024    1   tcp  46703  status
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  48417  nlockmgr
    100021    3   udp  48417  nlockmgr
    100021    4   udp  48417  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  45105  nlockmgr
    100021    3   tcp  45105  nlockmgr
    100021    4   tcp  45105  nlockmgr
    100005    1   udp  44051  mountd
    100005    1   tcp  60568  mountd
    100005    2   udp  44051  mountd
    100005    2   tcp  60568  mountd
    100005    3   udp  44051  mountd
    100005    3   tcp  60568  mountd
    100011    1   udp    997  rquotad
    100011    2   udp    997  rquotad
    100011    1   tcp    998  rquotad
    100011    2   tcp    998  rquotad

# rpcinfo -p 192.168.1.4
No remote programs registered.
Eh? something is blocking this somewhere :(


/etc/hosts.deny:
This is empty


# ufw status
Firewall not loaded

# showmount -e 127.0.0.1
Export list for 127.0.0.1:
/home/my/Desktop/HOME-NETWORK 192.168.1.200


However these commands won't return anything useful and the NFS mount cannot be mounted by the client 192.168.1.200

# showmount -e
portmap getport: RPC: Success
# showmount -e axe
portmap getport: RPC: Success

Any idea what went wrong?

Cheers, z

---

### Post by zong1 on 2009-06-29
Found problem.  hosts.deny was not empty. In fact, it was blocking.  I had concatonated hosts.allow, which is empty. D'oh.  Now have:

# rpcinfo -p 192.168.1.4
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  45941  status
    100024    1   tcp  46703  status
    100011    1   udp    997  rquotad
    100011    2   udp    997  rquotad
    100011    1   tcp    998  rquotad
    100011    2   tcp    998  rquotad
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100021    1   udp  40954  nlockmgr
    100021    3   udp  40954  nlockmgr
    100021    4   udp  40954  nlockmgr
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   tcp  60583  nlockmgr
    100021    3   tcp  60583  nlockmgr
    100021    4   tcp  60583  nlockmgr
    100005    1   udp  35141  mountd
    100005    1   tcp  56251  mountd
    100005    2   udp  35141  mountd
    100005    2   tcp  56251  mountd
    100005    3   udp  35141  mountd
    100005    3   tcp  56251  mountd


...So all is well.  Silly ol' me.

---

