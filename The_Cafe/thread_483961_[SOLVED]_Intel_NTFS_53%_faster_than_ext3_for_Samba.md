---
title: "[SOLVED] Intel: NTFS 53% faster than ext3 for Samba servers"
date: 2007-06-25
forum: The Cafe
---

### Post by altonbr on 2007-06-25
Main article: [http://softwarecommunity.intel.com/articles/eng/1259.htm](http://softwarecommunity.intel.com/articles/eng/1259.htm)

If NTFS is "53%" faster due to less fragmentations, then what file system is recommended for an Ubuntu server? Doesn't Ubuntu install ext3 by default? And I thought ext3 had journaling and NTFS didn't. I don't recall the last time I had to defrag my ext3 partition.

---

### Post by Zzl1xndd on 2007-06-25
After reading it I think its trying to say that its faster when Dealing with Windows based machies as they are assuming that the other machine uses NTFS and thus causes this problem.

---

### Post by prizrak on 2007-06-25
Samba on Windows is actually faster than on Linux. This is from personal experience between Linux-to-Linux, Windows-to-Windows and Windows-to-Linux. Asynchronous NFS is loads faster than Samba though :)

---

### Post by nalmeth on 2007-06-25
I've found that the router is the biggest factor in Samba performance. I don't fully understand, but I have one router that apparently has to send a query to each and every PC, and have it returned before the shares will appear. In other words it has to use bandwidth across all PC's that are plugged in.

Our new VOIP router handles these connections differently, Samba shares appear instantly. Anyone understand that?

---

### Post by jrusso2 on 2007-06-25
It would appear that there is some kind of misunderstanding in the translation of writting the files from Samba to EXT 3 that results in them being fragmented.

The article says there is no problem with XFS, and that defragmenting the ext 3 drive by recopying the files resulted in the performance loss being recovered.

---

### Post by Enverex on 2007-06-25
Samba suffers from general awful performance on Linux anyway. Use NFS whenever possible.

---

### Post by mips on 2007-06-25
> **nalmeth said:**
> I've found that the router is the biggest factor in Samba performance. I don't fully understand, but I have one router that apparently has to send a query to each and every PC, and have it returned before the shares will appear. In other words it has to use bandwidth across all PC's that are plugged in.

Our new VOIP router handles these connections differently, Samba shares appear instantly. Anyone understand that?

Huh, if the machines are on the same network what do you need a router for ? Nothing gets routed if it is the same network, you can unplug the router and all should carry on working.

---

### Post by altonbr on 2007-06-26
> **mips said:**
> Huh, if the machines are on the same network what do you need a router for ? Nothing gets routed if it is the same network, you can unplug the router and all should carry on working.

You mean modem correct?

---

### Post by JohnOfSheffield on 2007-06-26
XFS is great, so complex that nobody really understands it though. :D

Don't use it if you do not have backup power, it can and will trash your filesystem if shutdown incorrectly (it wasn't intended for the x86 architecture when it was created).

NTFS isn't as bad as every noob who just converted to Linux think it is, the constant defragging only ever adds performance in the users mind, Ext3 and others get just as fragmented (or more) but there are other things to consider when it comes to filesystems than fragmentation.

---

### Post by JohnOfSheffield on 2007-06-26
> **Enverex said:**
> Samba suffers from general awful performance on Linux anyway. Use NFS whenever possible.

Generally, SMB is faster than NFS even in *nix from what i have seen and tested.

---

