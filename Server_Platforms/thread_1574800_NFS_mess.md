---
title: "NFS mess"
date: 2010-09-14
forum: Server Platforms
---

### Post by nicolasdiogo on 2010-09-14
hi,

i am trying to setup NFS server but i keep getting this strange behaviour.



```

the /etc/exports contains

/export/myCloudZone01/storage01
192.168.1.0/255.255.255.0(async,insecure,no_subtree_check,fsid=0,rw)
/export/myCloudZone01/storage02
192.168.1.0/255.255.255.0(async,insecure,no_subtree_check,fsid=0,rw)

```


server configuration

```

$ cat /etc/default/nfs-kernel-server 

# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information, 
# see rpc.mountd(8) or http://wiki.debian.org/?SecuringNFS
RPCMOUNTDOPTS=--manage-gids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=no

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=

```


while the client
```

chefao@atlas:~$ cat /etc/default/nfs-common 
# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or http://wiki.debian.org/?SecuringNFS
STATDOPTS=

# Do you want to start the idmapd daemon? It is only needed for NFSv4.
NEED_IDMAPD=yes

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=no

```


i have created the following LVMs
```

# ls -l /export/myCloudZone01/storage0*
/export/myCloudZone01/storage01:
total 16
drwx------ 2 cloud cloud 16384 2010-09-12 15:41 lost+found
-rw-r--r-- 1 cloud cloud     0 2010-09-12 17:08 thisIsStorage01.txt

/export/myCloudZone01/storage02:
total 16
drwx------ 2 cloud cloud 16384 2010-09-12 17:22 lost+found
-rw-r--r-- 1 root  root      0 2010-09-12 23:38 thisIsStorage02.txt

```


to make sure i know which share i have loaded i created a file uniquely name in each LVM.

but when trying to load one share i get the other (it seems impossible to actually mount share storage02 as i always get storage01)

see below:
```

# mount localhost:/export/myCloudZone01/storage02/ /mnt/
# ls -l /mnt/
total 16
drwx------ 2 cloud cloud 16384 2010-09-12 15:41 lost+found
-rw-r--r-- 1 cloud cloud     0 2010-09-12 17:08 thisIsStorage01.txt

```


does anyone  understand what i am getting wrong here?

many thanks,


Nicolas

---

### Post by nicolasdiogo on 2010-09-15
bumping this post..

really need help here.

i am sure it is something simple but i can not see the wood between the trees

---

### Post by Metabaron on 2010-10-18
> **nicolasdiogo said:**
> hi,

```

the /etc/exports contains

/export/myCloudZone01/storage01
192.168.1.0/255.255.255.0(async,insecure,no_subtree_check,fsid=0,rw)
/export/myCloudZone01/storage02
192.168.1.0/255.255.255.0(async,insecure,no_subtree_check,fsid=0,rw)

```


My guess is that stating the same fsid twice will create some problems.
Try something like this and read the README file in /usr/share/doc/nfs-common.

```

/export
192.168.1.0/255.255.255.0(async,insecure,no_subtree_check,fsid=0,rw)
/export/myCloudZone01/storage01
192.168.1.0/255.255.255.0(async,insecure,no_subtree_check,fsid=100,rw)
/export/myCloudZone01/storage02
192.168.1.0/255.255.255.0(async,insecure,no_subtree_check,fsid=101,rw)

```

---

### Post by nicolasdiogo on 2010-10-18
i look forward to the day i get to know this much..

yep you are right i had given up using this 

but you are correct and i am not alone on that:
[http://www.linuxquestions.org/questions/linux-general-1/pulling-my-hair-out-over-nfs-fsids-769504/](http://www.linuxquestions.org/questions/linux-general-1/pulling-my-hair-out-over-nfs-fsids-769504/)

many thanks Metabaron for clarifying the problem.

with regards,

Nicolas

---

### Post by HermanAB on 2010-10-19
Probably the best solution is don't specify the fsid and let NFS create a unique number by itself.  This is explained clearly in the man page:
[http://linux.die.net/man/5/exports](http://linux.die.net/man/5/exports)

---

### Post by nicolasdiogo on 2010-10-19
fair point.

but since i did not understand NFS, i tried reading the docs on ubuntu:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

and i got confused with the usage of fsid


thanks for clarifying the issue.


Nicolas

---

