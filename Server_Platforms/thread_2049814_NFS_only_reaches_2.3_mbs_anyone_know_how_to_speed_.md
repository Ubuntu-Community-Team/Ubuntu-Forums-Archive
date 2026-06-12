---
title: "NFS only reaches 2.3 mb/s anyone know how to speed it up?"
date: 2012-08-29
forum: Server Platforms
---

### Post by androssofer on 2012-08-29
Hi,

so I have 2 computers, both running ubuntu 12.04.


On 1 I have set up an nfs share, and the other mounts this share.

the computer acting as the nfs server is wired to my router via gigabit ethernet.

The client is on wireless. 

however NFS only seems to reach 2.3 mb/s..

where as sshfs (mounted through nautilus) often reaches 5 mb/s..

anyone any ideas?

I tried tweaking the rsize and wsise, however it didnt make much of a difference.. 

export variables are as follows:

```
(rw,fsid=0,crossmnt,nohide,insecure,no_root_squash,no_subtree_check,no_wdelay,sync)
```

and

```
(rw,crossmnt,nohide,insecure,no_root_squash,no_subtree_check,no_wdelay,sync)
```

---

### Post by androssofer on 2012-08-30
bumpy bump

---

### Post by stmiller on 2012-08-30
Typically NFS is much faster than ssh / sshfs. Are both machines running the stock Ubuntu kernel?

---

### Post by androssofer on 2012-08-31
yeah both plain old Ubuntu desktop 12.04. 

I thought it might have been because the files where on a fat32 partition (external HD, usb 3), so moved a few to the Ubuntu ext4 partition and got the same speed...

network card issue perhaps? 

The MTU on the router is set at 1500, as thats the largest its supports.. so maybe dropped packets due to fragmentation?

---

### Post by SeijiSensei on 2012-08-31
Try adding "rsize=32768,wsize=32768" to the options in the NFS entry in the *client's* fstab.  Also "async" is typically much faster than "sync".  On stable networks, the potential loss of data is pretty small.

---

### Post by androssofer on 2012-09-02
> **SeijiSensei said:**
> Try adding "rsize=32768,wsize=32768" to the options in the NFS entry in the *client's* fstab.  Also "async" is typically much faster than "sync".  On stable networks, the potential loss of data is pretty small.

the async seems to have brought it up to about 5mb/s

was expecting more, but its enough for HD video :-).

---

