---
title: "Recommendation on vmware server 2.0.2 and ext4"
date: 2009-11-09
forum: Virtualisation
---

### Post by corrosion on 2009-11-09
Hello all,

Last week I was becoming crazy because 2 virtual machines were shutting down unexpectedly. I found that it happened every time I tried to move large files via networking from virtual machines to host machine (NFS, FTP) or from virtual machine to virtual machine. Since my server has 3 big hdds, i formatted one into ext3 (all of them were ext4) and moved the virtual machines into the ext3 hard disk. It was like magic. No more problems.
I post this here in the hope it can be useful for someone and I will look how to notify about this problem to vmware/ubuntu.

Regards,

PD: Host is 64bit 9.10 ubuntu server.

---

### Post by chrisguoado on 2009-11-11
Seems the problem has nothing to do with vmware, since it also happens between my 32-bit karmic on a real box and a Windows XP.
So we can say it is an ext4 related problem?

---

### Post by moontumbo on 2010-05-26
I seem to be seeing the same thing.  I have some vmware containers on an ext4 partition and they're having severe performance issues, causing the load to go sky high.  I'm glad to know there's somebody else experiencing this.

---

