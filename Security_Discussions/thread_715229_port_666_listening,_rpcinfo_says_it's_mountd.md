---
title: "port 666 listening, rpcinfo says it's mountd"
date: 2008-03-04
forum: Security Discussions
---

### Post by talz13 on 2008-03-04
I finally installed nmap today to check out my local services, and noticed:

```

Not shown: 1664 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
443/tcp   open  https
445/tcp   open  microsoft-ds
**666/tcp   open  doom**
2049/tcp  open  nfs
3128/tcp  open  squid-http
3306/tcp  open  mysql
5900/tcp  open  vnc
10000/tcp open  snet-sensor-mgmt
32776/tcp open  sometimes-rpc15
50000/tcp open  iiimsf

```

```
$ rpcinfo -p $HOSTNAME
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100021    1   udp  32771  nlockmgr
    100021    3   udp  32771  nlockmgr
    100021    4   udp  32771  nlockmgr
    100021    1   tcp  53893  nlockmgr
    100021    3   tcp  53893  nlockmgr
    100021    4   tcp  53893  nlockmgr
    100005    1   udp    663  mountd
    100005    1   tcp    666  mountd
    100005    2   udp    663  mountd
    100005    2   tcp    666  mountd
    100005    3   udp    663  mountd
    100005    3   tcp    666  mountd
    100024    1   udp  32772  status
    100024    1   tcp  40490  status

```

After some investigation (rpcinfo -p $HOSTNAME), it looks like TCP port 666 and UDP port 663 are being used by mountd.  Does that seem correct?  I think I was just scared by the label of **doom** that nmap gave it, but apparently it just lists services by their accepted use?  Like a server running on port 22 will be listed as an SSH server, even if it's not?

Hopefully I'm just a bit spooked, but I just wanted to check on this port...

---

### Post by wirelessmonkey on 2008-03-04
Yep, it looks good. NFS (mountd) is often configured to use TCP 666.

---

### Post by talz13 on 2008-03-05
That's good, I was just kind of freaking out yesterday when I saw this **DOOM** port open for no apparent reason ](*,)

---

