---
title: "nfs4: Hide content of subdirectory"
date: 2010-10-23
forum: Server Platforms
---

### Post by Sitron_NO on 2010-10-23
I have installed Ubuntu Server on a network with different Ubuntu clients (192.168.10.0/24). I want all clients to be able to mount some NFSv4 exported directories, while other clients can mount all NFSv4 exported directories. However, if a client can not mount a directory, it should not be able to list it contents.

So I followed [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) and made this exports-file:
```
/opt/exports/nfs          192.168.10.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/opt/exports/nfs/home     192.168.10.10/32(rw,no_root_squash,insecure,no_subtree_check,async,hide)
/opt/exports/nfs/public   192.168.10.0/24(rw,all_squash,insecure,subtree_check,async,anonuid=150,anongid=100)

```The contents of /opt/exports/nfs on the server is: *home*, *home.old* and *public*.

If I am on a client (say 192.168.10.111) I can mount nfssever:/ and in this directory and can see all three directories (*home*, *home.old* and *public*), I can list the contents and read the files (those with a a+r permission), even they all are all mapped to nobody/nogroup. But this is not want I want: I want that client to only list the content of the root-directory, and nothing else. However, at a later stage, he will be able to mount nfsserver:/public

Is this possible?

---

