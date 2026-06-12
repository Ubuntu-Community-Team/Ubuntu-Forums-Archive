---
title: "Nfs"
date: 2009-11-06
forum: Server Platforms
---

### Post by hirohitosan on 2009-11-06
Hi there!
I just installed Ub9.1. I installed NFS server + client for transferring files. I have another FreeBSD box where I have both NFS server and client. I cannot write/delete files on mu Ub box.

On Ububtu /etc/exports

```
/home/my-folder    free.bsd.server(rw,sync,no_root_squash)
```

how can I set my NFS server to write on home folder

tahnks

---

### Post by karlson on 2009-11-06
> **hirohitosan said:**
> Hi there!
I just installed Ub9.1. I installed NFS server + client for transferring files. I have another FreeBSD box where I have both NFS server and client. I cannot write/delete files on mu Ub box.

On Ububtu /etc/exports

```
/home/my-folder    free.bsd.server(rw,sync,no_root_squash)
```

how can I set my NFS server to write on home folder

tahnks

I assume you have mounted the share.  Do the userIDs match across machines?

---

### Post by Bucky Ball on 2009-11-06
What have you got in your /etc/fstab to mount the share? It should look something like this on the client machine but with your details:

```
# Entry for /server/media/your_share
192.168.0.102:/media/your_share /media/local_mountpoint_for_share nfs users,rsize=8192,wsize=8192,timeo=14,intr

```... where IP is the static IP of the other server. You don't need this so omit if you are not running with static IPs. You may need to run something to resolve DNS if this is the case. Hope that is of some help.

---

### Post by hirohitosan on 2009-11-07
> **karlson said:**
> I assume you have mounted the share.  Do the userIDs match across machines?
yes, of course. I can copy but I cannot write. The users ID are the same.

I have other two FreeBSD machines and with same user ID and I can also write on the mounted volume, but here I got "permission denied" message when I try to write.

---

### Post by hirohitosan on 2009-11-07
> **Bucky Ball said:**
> What have you got in your /etc/fstab
nothing I didn't modify the fstab. I just mount the volume like this:
(on BSD machine, client)
```
# mount ubuntu.nfs.server:/home/my-folder /mnt/my-share/
```

and the volume was mounted successfully, but I cannot write (delete) on server export directory

---

