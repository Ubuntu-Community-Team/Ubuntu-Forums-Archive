---
title: "nfs server: clnt_create: RPC: Port mapper failure - RPC: Unable to receive"
date: 2011-12-26
forum: Server Platforms
---

### Post by jaskirat on 2011-12-26
Hi a everyone.

I'm trying to setting up a nfs server.
I have ubuntu 10.04 on each pc.

Server ip: 192.168.0.109
Client ip: 192.168.0.105

I have done these things:

1) apt-get install nfs-kernel-server nfs-common
2) I create a folder with the right "rights"
3) then I add to /etc/exports:
```
/export       192.168.0.1/255.255.255.0(rw,async,no_subtree_check)
#/export       192.168.0.105(rw,async,no_subtree_check)
```4) and I restarted service: sudo /etc/init.d/nfs-kernel-server restart
5) then I try to run these command:
```
rpcinfo -p
``` --> it returns to me:
```
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  54418  status
    100024    1   tcp  52526  status
    100021    1   udp  54993  nlockmgr
    100021    3   udp  54993  nlockmgr
    100021    4   udp  54993  nlockmgr
    100021    1   tcp  45037  nlockmgr
    100021    3   tcp  45037  nlockmgr
    100021    4   tcp  45037  nlockmgr
    100003    2   udp   2049  nfs
    100003    3   udp   2049  nfs
    100003    4   udp   2049  nfs
    100003    2   tcp   2049  nfs
    100003    3   tcp   2049  nfs
    100003    4   tcp   2049  nfs
    100005    1   udp  38283  mountd
    100005    1   tcp  53864  mountd
    100005    2   udp  38283  mountd
    100005    2   tcp  53864  mountd
    100005    3   udp  38283  mountd
    100005    3   tcp  53864  mountd
```6) Then if I do: ```
showmount -e
``` it says to me:
```
clnt_create: RPC: Port mapper failure - RPC: Unable to receive
```7) I've also tried to do:
```
service portmap restart
``` --> that says:
```
portmap start/running, process 812
```8 ) I've also open all the port (nfs, mountd, portmapper) of my router (for server 192.168.0.109)

BUT

```
showmount -e
``` return always:
```
clnt_create: RPC: Port mapper failure - RPC: Unable to receive
```The same string is returned from client if I do: ```
showmount -e 192.168.0.109
```What I can do?

====================================================
ADDITIONAL INFO:

```
#showmount -e localhost
``` --> return:
```
Export list for localhost:
/data   192.168.0.0/24
/export 192.168.0.1/255.255.255.0
```===

```
#netstat -plntu
``` --> return:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -              
tcp        0      0 0.0.0.0:60677           0.0.0.0:*               LISTEN      2744/rpc.statd 
tcp        0      0 0.0.0.0:51785           0.0.0.0:*               LISTEN      2947/rpc.mountd
tcp        0      0 0.0.0.0:41837           0.0.0.0:*               LISTEN      -              
tcp        0      0 127.0.0.1:111           0.0.0.0:*               LISTEN      2724/portmap   
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      1651/vsftpd    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      707/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1194/cupsd     
tcp6       0      0 :::22                   :::*                    LISTEN      707/sshd       
tcp6       0      0 ::1:631                 :::*                    LISTEN      1194/cupsd     
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -              
udp        0      0 0.0.0.0:60566           0.0.0.0:*                           -              
udp        0      0 0.0.0.0:60060           0.0.0.0:*                           939/avahi-daemon: r
udp        0      0 0.0.0.0:800             0.0.0.0:*                           2744/rpc.statd 
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1596/dhclient  
udp        0      0 0.0.0.0:69              0.0.0.0:*                           2283/xinetd    
udp        0      0 0.0.0.0:57809           0.0.0.0:*                           2744/rpc.statd 
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           939/avahi-daemon: r
udp        0      0 127.0.0.1:111           0.0.0.0:*                           2724/portmap   
udp        0      0 0.0.0.0:47100           0.0.0.0:*                           2947/rpc.mountd

```==

```
# sudo iptables -L
``` --> return:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination        

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination        

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```==
(on CLIENT)
```
# mount 192.168.0.109:/export /mnt/import
``` --> return
```
mount.nfs: mount system call failed
```

---

### Post by SeijiSensei on 2011-12-27
The clients need to have nfs-common installed as well.  Did you do that?

---

### Post by jaskirat on 2011-12-28
> **SeijiSensei said:**
> The clients need to have nfs-common installed as well.  Did you do that?
Yes I have done it.

---

### Post by rduke15 on 2012-05-24
I had this error when my Debian NFS server had, in /etc/default/portmap :

OPTIONS="-i 127.0.0.1"

So it was not listening on the ethernet interface. Commenting out the line solved the problem.

---

### Post by lisati on 2012-05-24
Old thread closed

---

