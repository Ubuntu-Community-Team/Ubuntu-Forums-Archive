---
title: "Virus scanning Windows"
date: 2007-05-16
forum: Server Platforms
---

### Post by pockets on 2007-05-16
Hi, I have Ubuntu and Windows XP on my laptop. Unfortunately I wa connected to the internet through XP (pre- service pack 2 version) and now Windows is riddled with viruses. What's a good Linux virus-scanner that will be able to scan the Windows partition? Thanks.

---

### Post by Ziox on 2007-05-16
apt-cache search virus scanner

that ought to return some results.  I know there is ClamVS....

However a problem with scanning windows is that since linux doesn't have native NTFS writing support, you can't delete the Virus from within Linux, unless you enable NTFS support (unstable).

---

### Post by dxdemetriou on 2007-05-16
not exactly unstable,
there is the ntfs-3g, as I know is open-source and works very well for ntfs partitions. It is only limited to half speed from when it works native
the problem is with linux antivirus, if can recognize those viruses. I don't know about the clamvs, but I think antivir can do it.
Somebody more expert maybe help :)

---

### Post by Ziox on 2007-05-16
that reminds, avg has a linux scanner, go to their site and check it out.

---

