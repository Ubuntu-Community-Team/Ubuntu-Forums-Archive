---
title: "[NFS]Set higher value in /proc/fs/nfsd/max_block_size"
date: 2011-03-24
forum: Server Platforms
---

### Post by deejaylinux on 2011-03-24
Hi ubunters,

I'm trying to check different NFS configurations to set the best one giving me good performance.

I would like to work with rsize and wsize values greater than 64Kb, but I can't because that is the maximum size set at kernel level (value in /proc/fs/nfsd/max_block_size file).

Is it possible to change this value in any way? I don't see a proper kernel variable to do it (through sysctl), and it seems it's not possible to redirect an 'echo' to this file.

Hope you can help in some manner!

Thanks and regards!

---

### Post by rubylaser on 2011-03-24
Why don't you set the block size on the client side for the mount point.   This is the way this is typically done.

[http://www.debianhelp.co.uk/nfs.htm]("http://www.debianhelp.co.uk/nfs.htm")

---

### Post by deejaylinux on 2011-03-25
Yeah! that's the thing I did, but doesn't matter the number I set in rsize or wsize, after checking the real values used (cat /proc/mounts) I see I can't go beyond the value registered in the file /proc/fs/nfsd/max_block_size on the server.

Any other ideas?

Thanks in advance guys!

---

### Post by rubylaser on 2011-03-25
I've never tried to change that value, and you can't echo values to it as you suggested.  I'm not sure why you're trying to do this though?  With that default value, I can completely saturate a gigabit connection to my mdadm RAID array.  Are you trying change this value because you're seeing poor performance across the network?

---

### Post by deejaylinux on 2011-03-25
I would like to do several performance tests. For instance, I would like to know which scenario is better: to have more system calls (everytime you read/write a block from/to disk) while working with big files structures or to have more fragmentation in transfers (the biggest block you read/write the biggest fragmentation you have at eth level).

My store back-end is a LVM on IDE disks and I think the more system calls the worst performance I get.

Maybe the only way to get higher values is a kernel compilation, isn't it?

Thanks for your help @rubylaser :)

---

### Post by rubylaser on 2011-03-25
I think you'd need a patched version of nfsd, but I really don't think you're going to see any improvement from that.  Here's some info about patches for nfsd.

[http://lists.community.tummy.com/pipermail/linux-ha-dev/2009-July/016642.html]("http://lists.community.tummy.com/pipermail/linux-ha-dev/2009-July/016642.html")

---

### Post by mlord on 2011-06-12
Actually, one can echo new values directly into **/proc/fs/nfsd/max_block_size**, except it only seems to allow doing so when the NFS server is not running.

So stop NFS, change the value, then restart NFS:

[B][FONT="Fixedsys"]     /etc/init.d/nfs-kernel-server stop
     echo 65536 > /proc/fs/nfsd/max_block_size
     /etc/init.d/nfs-kernel-server start[/FONT][/B]

(or use the newfangled upstart commands if you like).

To make the change more permanent for future system startups, you can stuff the **echo** line into **/etc/default/nfs-kernel-server**

I've noticed that newer systems/kernels seem to begin with a MUCH TOO LARGE value in that variable, causing the ethernet link to get choked whenever copying a large file from host to host over NFS.  So here, I've had to reduce the default (256K) down to a more sensible 32768.

Cheers

---

