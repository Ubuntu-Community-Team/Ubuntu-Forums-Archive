---
title: "NFS performance - client timeouts"
date: 2012-08-28
forum: Server Platforms
---

### Post by td3201 on 2012-08-28
Hello,

I have a pretty busy NFS server on 12.04. We are seeing client timeouts such as:
[I]nfs: server omadvnfs01-nfs-a not responding, still trying
nfs: server omadvnfs01-nfs-c not responding, still trying[/I]

1. We are using MTU 9000
2. Mounting with these options:  defaults,noatime,nodiratime 
3. Exporting with these options: rw,no_root_squash,async,no_subtree_check
4. Modified RPCNFSDCOUNT in /etc/default/nfs-kernel-server to be 64.  

We push around 650 Mbps through this server using 802.3ad bonded nics. But hit up to 1 Gbps speeds.  I think our clients need to send more.  Any ideas?

---

### Post by SeijiSensei on 2012-08-29
Try adding "rsize=32768,wsize=32768" to the client's list of options in fstab.  You might try upping the values to 65536 or even higher and see how performance is affected.

Take a look at [this document](http://nfs.sourceforge.net/nfs-howto/ar01s05.html) for more information on optimizing throughputs.

---

