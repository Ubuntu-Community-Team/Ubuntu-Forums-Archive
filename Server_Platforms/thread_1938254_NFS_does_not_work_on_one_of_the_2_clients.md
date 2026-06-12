---
title: "NFS does not work on one of the 2 clients :|"
date: 2012-03-09
forum: Server Platforms
---

### Post by JBtje on 2012-03-09
Hello all,
 
I have this problem for a couple of weeks now, sometimes i am able to get the NFS server to work, but moslty i keep searching the internet for a solution. however, i have still not found any :|
 
```

[COLOR=black]root@myServer-files:/[/COLOR][COLOR=black]# mount -t nfs -o rw,defaults,nfsvers=3 192.168.1.50:/media/External/ /media/External[/COLOR]
 
[COLOR=black]mount.nfs: access denied by server while mounting 192.168.1.50:/media/External[/COLOR]
 
 
[COLOR=black]root@myServer-files:/# mount -t nfs4 -o rw,defaults 192.168.1.50:/ /media/External[/COLOR]
[COLOR=black]mount.nfs4: mounting 192.168.1.50:/ failed, reason given by server:[/COLOR]
[COLOR=black]No such file or directory[/COLOR]

```
 
Well.. trying NFS 3 and 4, both failing...
 
 
RPCinfo gives:
```

rpcinfo -p
   program vers proto   port
    100000    2   tcp    111  portmapper
    100000    2   udp    111  portmapper
    100024    1   udp  47865  status
    100024    1   tcp  52748  status

```
 
Note that: nlockmgr is not running, do i need it? how do i get in running (/etc/init.d/nfslock does not exist) so, how do i install it?
 
 
Showmount gives:
```
showmount 130.89.148.210 -e
Export list for 192.168.1.50:
/[COLOR=black]media/External/[/COLOR]          192.168.1.51,192.168.1.100
/media/Ecternal2/         192.168.1.100

```
 
The Ubuntu server running at 192.168.1.100, IS able to mount both the NFS, via version 3... so the NFS server is working, but why is the client at 192.168.1.51 not working???
 
 
Thanks.
Jeffrey

---

### Post by JBtje on 2012-03-10
I installed a new server, and tried to mount the disk again. Also this time i gain the "mount.nfs: access denied by server while mounting"
 
I installed showmount, and printed the showmount -e message for the NFS server, well.. as i could have known, tje new VM's IP address did not match the ones in /etc/exports on the fileserver.
 
Arriving at the /etc/exports file on the fileserver, I reallized that I was trying to share the same directory via 2 lines...
 
```

/[COLOR=black]media/External/[/COLOR]  192.168.1.100(rw,no_root_squash,async,acl)
/[COLOR=black]media/External/[/COLOR]  192.168.1.51(rw,no_root_squash,async,acl)

```
 
Even though showmount -e tells me that the directory "/[COLOR=black]media/External/[/COLOR]" was accessable by both IP's, it did not allow me to access the directory from IP.51
 
I have now commented out the IP .100 in the /etc/exports file, and it works (I can mount it on the IP.51 system).
 
but Why ? Should i have merged the lines to one? and in that case, how?
 
Thanks,
Jeffrey

---

### Post by nanog on 2012-03-10
Are you running lucid? It looks like there is bug in nfs that is preventing mounts unless you specify the nfs version-- there is a new kernel in proposed that may address this bug.

To be honest I fixed the issue by upgrading my last lucid server to precise. (I need some deps that I would have to compile for lucid anyways.)

---

