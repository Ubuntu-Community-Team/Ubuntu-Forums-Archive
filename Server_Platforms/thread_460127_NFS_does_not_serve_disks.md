---
title: "NFS does not serve disks"
date: 2007-05-31
forum: Server Platforms
---

### Post by BillDozer on 2007-05-31
Hi,

I have a problem with my new server.

I have a server with 4 disks, and I am just figuring out how to set it up. Just to check it I created a folder called /sharedData which I serve with NFS.

/etc/exports
```

/sharedData    192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
```
/etc/fstab
```

/dev/sdb1 /sharedData/disk2  ext3  rw,defaults  0   2
/dev/sdc1 /sharedData/disk3  ext3  rw,defaults  0   2
/dev/sdd1 /sharedData/disk4  ext3  rw,defaults  0   2
```

When I look into the disk folders on the server it looks ok.

When I look into the disk folders from the client it is wrong, when I create/copy a file into it the file cannot be seen on the server.

When I unmount the disks, I can see the files created from the client.

What am I doing wrong?

Thx.

---

### Post by EmmEff on 2007-06-01
Export the drives individually in /etc/exports.  I thought NFS would be able to cross-filesystems within a single mount point but obviously not well.  What client are you using?

---

### Post by BillDozer on 2007-06-01
Yes that works, but it is not what I wanted :-( I'm using feisty as a client

---

### Post by EmmEff on 2007-06-02
You can work around the problem using autofs on the client:

/etc/auto.master:

```

/sharedData auto.sharedData

```

/etc/auto.sharedData:

```

disk1 server:/sharedData/disk1
disk2 server:/sharedData/disk2
disk3 server:/sharedData/disk3
disk4 server:/sharedData/disk4

```

/sharedData is the pseudo parent directory.

AutoFS is really easy to setup and gives you the effect that you want.

---

### Post by BillDozer on 2007-06-04
Thx. I will try that.

---

