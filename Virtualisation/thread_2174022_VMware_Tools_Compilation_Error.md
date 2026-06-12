---
title: "VMware Tools Compilation Error"
date: 2013-09-12
forum: Virtualisation
---

### Post by alan-r-barker on 2013-09-12
I am running Ubuntu 13.10 (beta) with Linux Kernel 3.11.0-7 as a Guest OS under VMware Fusion 6.0.0 (1296151) on my Macbook (Mac OS X 10.8.4). I attempted to install VMware Tools 9.6.0 Build-1294478 and got the following errors during the shared folder configuration compile.


  CC [M]  /tmp/modconfig-j0IFhU/vmhgfs-only/inode.o
/tmp/modconfig-j0IFhU/vmhgfs-only/inode.c: In function ‘HgfsPermission’:
/tmp/modconfig-j0IFhU/vmhgfs-only/inode.c:1893:29: error: ‘struct dentry’ has no member named ‘d_count’
          int dcount = dentry->d_count;
                             ^
make[2]: *** [/tmp/modconfig-j0IFhU/vmhgfs-only/inode.o] Error 1
make[1]: *** [_module_/tmp/modconfig-j0IFhU/vmhgfs-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-5-generic'
make: *** [vmhgfs.ko] Error 2
make: Leaving directory `/tmp/modconfig-j0IFhU/vmhgfs-only'


I realise that Ubuntu and the Kernel are not finalised but didn't see this problem until Ubuntu Update-Manager installed the 3.11 Kernel series. Any ideas how to overcome this issue appreciated.

---

### Post by Toz on 2013-09-12
Hello and welcome to the forums.

Since 13.10 hasn't yet been released, I'm going to move this thread to the more apropriate **U+1**.

---

### Post by QB89Dragon on 2013-10-22
> **Toz said:**
> Hello and welcome to the forums.

Since 13.10 hasn't yet been released, I'm going to move this thread to the more apropriate **U+1**.

This issue is still present on Ubuntu 13.10 now it has been released. I am also receiving the same error. Maybe this thread can now be moved somewhere where it will be noticed?

---

### Post by cariboo on 2013-10-22
Moved

---

### Post by hydra3333 on 2013-10-28
maybe this is similar
[http://ubuntuforums.org/showthread.php?t=2184195](http://ubuntuforums.org/showthread.php?t=2184195)

---

### Post by alan-r-barker on 2013-10-28
> **hydra3333 said:**
> maybe this is similar
[http://ubuntuforums.org/showthread.php?t=2184195](http://ubuntuforums.org/showthread.php?t=2184195)

Yes it is and the fix works, thanks!

---

