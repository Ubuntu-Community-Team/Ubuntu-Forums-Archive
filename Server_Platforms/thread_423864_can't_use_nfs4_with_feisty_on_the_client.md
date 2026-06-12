---
title: "can't use nfs4 with feisty on the client"
date: 2007-04-26
forum: Server Platforms
---

### Post by deuce868 on 2007-04-26
I'm working on setting up an nfs share on a home network. I have an external drive mounted as /filestorage and created some directories in there. 

My main trouble is using nfs4. If I mount it like so:

> 192.168.0.10:/filestorage/shared    /home/rharding/filestorage/shared   nfs4    rw,bg  0   0

I get the following error when I try 'mount -a'

> Warning: rpc.idmapd appears not to be running.
         All uids will be mapped to the nobody uid.
mount: special device 192.168.0.10:/filestorage/shared does not exist

Yet it is running. 

> $ ps aux | grep rpc
statd    13285  0.0  0.0   1836   748 ?        Ss   08:05   0:00 /sbin/rpc.statd
root     13301  0.0  0.0   3648   608 ?        Ss   08:05   0:00 /usr/sbin/rpc.idmapd
root     15656  0.0  0.0      0     0 ?        S<   09:00   0:00 [rpciod/0]
rharding 15916  0.0  0.0   2884   752 pts/1    R+   09:06   0:00 grep rpc

If I change the mount line to force using nfs version 3 it mounts up and works fine. 
> 192.168.0.10:/filestorage/shared    /home/rharding/filestorage/shared   nfs    rw,nfsvers=3,bg  0   0

I found a few references, but nothing much on how to fix this. Any ideas is appreciated.

---

### Post by deepwalker on 2007-04-29
> **deuce868 said:**
> 
192.168.0.10:/filestorage/shared /home/rharding/filestorage/shared nfs4 rw,bg 0 0 

I'm think in your /etc/exports in export string is fsid=0? : ))
ok, try this:
192.168.0.10:/ /home/rharding/filestorage/shared nfs4 rw,bg 0 0 
:KS

---

### Post by khaeru on 2007-05-05
I'm also having this problem.

---

### Post by nihilist514 on 2007-06-17
Found this link that should get you in the write direction

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/87382](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/87382)

Talks about chagning the /etc/default/nfs-common file to look like this

STATDOPTS=
NEED_LOCKD=
NEED_IDMAPD=yes
NEED_GSSD=no

also creating a pid file 

24176 ? Ss 0:00 /usr/sbin/rpc.idmapd
root@spectrum:~ # echo 24176 > /var/run/rpc.idmapd.pid
root@spectrum:~ # mount -tnfs4 ying64:/ /mnt/ying64/
 -> works!

---

### Post by RaZoR1394 on 2007-06-30
I tried everything on the bugtracker and it won't work. I think I'm going to pull my hair out.

I followed the community guide located here, [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto) .

edit:

Seems I didn't try everything. I was looking inside /etc/default/nfs-common on the server not on the client as the advice said. Duh! I still get the idmapd message but the shares work.

---

