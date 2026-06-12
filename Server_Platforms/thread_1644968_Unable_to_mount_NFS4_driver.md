---
title: "Unable to mount NFS4 driver"
date: 2010-12-14
forum: Server Platforms
---

### Post by kamiru on 2010-12-14
I tried this command in a Ubuntu 10.10 server

$ sudo mount -t nfs4 -o port=99 xxx.xxx.xxx.xxx:/home /mnt/tmp

The server returns an error message "mount.nfs4: Protocol family not supported" and I have installed nfs-common. 

Could anyone tell me what I did wrong? Thanks!

---

### Post by amauk on 2010-12-14
NFSv4 is different from v3

Have you setup a root export directory on the server, and bind mounted your individual exports to the root export directory?

---

### Post by kamiru on 2010-12-14
I follow this page ([https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)) and have binded my home directory to "/export/me"

/etc/export in the server 
```
/export       client_ip/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/me  client_ip/24(rw,nohide,insecure,no_subtree_check,async)

```

In the client
```

$ sudo mount -t nfs4 -o proto=tcp,port=99 server_ip:/ /mnt/tmp
mount.nfs4: Protocol family not supported

```

---

### Post by amauk on 2010-12-14
> **kamiru said:**
> In the client
```

$ sudo mount -t nfs4 -o proto=tcp,port=99 server_ip:/ /mnt/tmp
mount.nfs4: Protocol family not supported

```Assuming it's not a copy/paste error, you've missed off the share directory

```
sudo mount -t nfs4 -o proto=tcp,port=99 server_ip:[COLOR="Red"]/me[/COLOR] /mnt/tmp
```

*edit*
also, what's with the port 99?
NFS is 2049 by default

---

### Post by kamiru on 2010-12-14
Thank you very much for your prompt reply first.

I have created a folder "/export/me" and blind it to my home directory in the server. So that the path "/me" can be mounted from the client computer.

Since port 2049 is blocked by my company, I changed the default port to 99 by editing /etc/default/nfs-kernel-server

```
RPCMOUNTDOPTS="--manage-gids --port 99"
```

I still have no idea why it shows this error message "mount.nfs4: Protocol family not supported" to me? I did search from Google and this forum and get no idea how to solve it.

---

### Post by kamiru on 2010-12-15
**mount.nfs4: Protocol family not supported**

I did search again from Google and found the same error message in an early version of Fedora. However, the solution doesn't apply to Ubuntu 10.10. 

Can anyone share the proper steps of mounting a NFS4 driver?

---

