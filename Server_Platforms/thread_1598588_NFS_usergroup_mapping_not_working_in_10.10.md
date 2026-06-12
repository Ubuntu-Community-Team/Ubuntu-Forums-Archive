---
title: "NFS user/group mapping not working in 10.10?"
date: 2010-10-16
forum: Server Platforms
---

### Post by paol05 on 2010-10-16
Hi,
I have the following strange situation after upgrading to 10.10 (both the NFS server and client are on 10.10):

To make UID and GID mapping trivial, I've made sure that clients and server all have the same users and groups with the same IDs. This used to work fine.

However now the client is always displaying 4294967294 for the UID and GID but - and here is the strange bit - if I create a file on the client it shows up on the server with the correct user and group (but on the client still with 4294967294).
It's as if the mapping is working fine int the client->server direction but wrong in the server->client direction...

Any ideas?

Here is the exports line on the server:
```
data/fileserver 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check)
```

And the fstab line on the client:
```
htpc:/data/fileserver /data/fileserver nfs defaults 0 0
```

Trying to chown a file on the client gives the error "chown: changing ownership of `somefile': Invalid argument"

---

### Post by basd82 on 2010-10-17
> **paol05 said:**
> Hi,
I have the following strange situation after upgrading to 10.10 (both the NFS server and client are on 10.10):

To make UID and GID mapping trivial, I've made sure that clients and server all have the same users and groups with the same IDs. This used to work fine.

However now the client is always displaying 4294967294 for the UID and GID but - and here is the strange bit - if I create a file on the client it shows up on the server with the correct user and group (but on the client still with 4294967294).
It's as if the mapping is working fine int the client->server direction but wrong in the server->client direction...

Any ideas?

Here is the exports line on the server:
```
data/fileserver 192.168.1.0/255.255.255.0(rw,sync,no_subtree_check)
```And the fstab line on the client:
```
htpc:/data/fileserver /data/fileserver nfs defaults 0 0
```Trying to chown a file on the client gives the error "chown: changing ownership of `somefile': Invalid argument"


THis is normal behaveyour of NFS , 

Jou need to have all user on both systems with the same gid en uid.

A way to acomplise this is NIS, in that case all user must be created on the server.

---

### Post by paol05 on 2010-10-17
basd82, you misread me, I *do* have all users and groups with the same ID...

---

### Post by Nephelauxetic on 2010-10-18
I have the same problem. The NFS server is a solaris server in my case. It used to work with older versions of Ubuntu without any problems and new I get UID and GID 4294967294 4294967294

Any solutions to this?

---

### Post by paol05 on 2010-10-18
If everyone is seeing this then a filing a bug report might be in order. (I searched the ubuntu bugs before posting this and didn't find anything related).

Can anyone else confirm seeing this behavior?

---

### Post by ewanmcdowall on 2010-10-18
Hi,

I'm getting this problem too.  The NFS server is also a solaris box and the mapping worked fine before my upgrade to 10.10.  I too am getting 4294967294 as the gid/uid.

---

### Post by paol05 on 2010-10-18
I filed bug #662711:

[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/662711](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/662711)

---

### Post by pt314 on 2010-10-21
This looks like rpc.idmapd isn't doing its job properly. Is it running on both machines? Do they both have the same Domain option in /etc/idmapd.conf?

---

### Post by quesy on 2010-10-21
Getting the same problem to, and im unable to solve this. This is very critical for me since i use autofs for all my users.

---

### Post by hplehn on 2010-10-22
using the option nfsvers=3 on the client fixes the problem for me.

---

### Post by David Tomic on 2010-10-24
I'm noticing the same problem as well, on two different machines which have just been upgraded to 10.10.

Another machine - which is still running 10.04 - works absolutely fine, so any time I need to change permissions I have to do it via that machine.

Kind of annoying ...

---

### Post by David Tomic on 2010-10-24
> **hplehn said:**
> using the option nfsvers=3 on the client fixes the problem for me.

Not sure that it's really a 'fix' when you have to downgrade to the previous version of a protocol - losing quite a few features in the process - but otherwise you're right, it does seem to remove this particular problem.

I'll use this as a workaround until the actual problem can be resolved.

Thank you for pointing it out ...

---

### Post by pfnguyen on 2010-10-25
I just posted the following comment on the bug at [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/662711/comments/6](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/662711/comments/6)

> 
Not a bug it seems, but needs documentation or something somewhere.

10.10 enables NFSv4 and I was able to fix it by enabling nfs idmap on both server and client.

On my solaris server, I edited /etc/default/nfs and set NFSMAPID_DOMAIN to my server's name (domain name, whatever), then did svcadm restart nfs/mapid

On ubuntu, I edited /etc/idmapd.conf and changed Domain to be the same value as what I set for NFSMAPID_DOMAIN, edit /etc/default/nfs-common and set NEED_STATD=no and NEED_IDMAPD=yes, then service rpc_pipefs restart and service idmapd restart, remount your nfs shares (in my case, service autofs restart); and all the uid/gid mapping should now be correct.


---

### Post by dsauter on 2010-11-11
> **David Tomic said:**
> Not sure that it's really a 'fix' when you have to downgrade to the previous version of a protocol - losing quite a few features in the process - but otherwise you're right, it does seem to remove this particular problem.

I'll use this as a workaround until the actual problem can be resolved.

Thank you for pointing it out ...

Would changing nfs to nfs4 for the system type work (in the /etc/fstab file), preserving all the nfs4 goodness?
 
i.e.
192.168.100.85:/data/altamonte   /mnt/test   nfs   rw   0   0

becomes
192.168.100.85:/data/altamonte   /mnt/test   **nfs4**   rw   0   0

More info on nfs4 mounting from:
[http://manpages.ubuntu.com/manpages/dapper/man5/nfs.5.html]("http://manpages.ubuntu.com/manpages/dapper/man5/nfs.5.html")

---

