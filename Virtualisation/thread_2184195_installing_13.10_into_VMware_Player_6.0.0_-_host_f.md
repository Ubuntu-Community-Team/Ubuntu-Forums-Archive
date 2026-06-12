---
title: "installing 13.10 into VMware Player 6.0.0 - host folder share issue"
date: 2013-10-28
forum: Virtualisation
---

### Post by hydra3333 on 2013-10-28
Warning: 
a windows user here; ie a total and absolute novice who can just about manage an "ls -al" 2 times out of 4.

Installing Ubuntu into VMWARE Player 6.0.0 results in a problem where the VMware tools won't share nominated Windows host's folder like it has in the past.
 
Grr. :mad: The issue has been known for at least 5 weeks and VMware haven't bothered to fix it in their VMware tools. :mad: Grr. 
VMware player is worth the price you pay for it, I guess.
[https://communities.vmware.com/message/2287722](https://communities.vmware.com/message/2287722)
In the same page, a fix is suggested. It works. Why VMware have been careless and slack, who knows.

In summary, 
1. From the player menu, attempt to re-install the VMware tools (Player, Manage, Re-install...)
That will give you a mounted CD with a tar thing which contains folder "vmware-tools-distrib"
2. Extract folder "vmware-tools-distrib" into your desktop $home/Desktop
3. On your desktop, create a small fix.sh with gedit, and then do a sudo chmod +x ./fix.sh to make it executable.
Content:
```
set -x
cd $home
cd Desktop
cd vmware-tools-distrib/lib/modules/source
sudo tar xf vmhgfs.tar
sudo wget https://raw.github.com/rasa/vmware-tools-patches/master/patches/vmhgfs/vmhgfs-d_count-kernel-3.11-tools-9.6.0.patch
sudo Patch -p0 <vmhgfs-d_count-kernel-3.11-tools-9.6.0.patch
sudo mv vmhgfs.tar vmhgfs.orig.tar
sudo tar cf vmhgfs.tar vmhgfs-only
cd $home
cd Desktop
cd vmware-tools-distrib
sudo ./Vmware-install.pl
set +x
```
The content of the patch should contain something like (it may not have pasted quite correctly below):
```
--- vmhgfs-only/inode.c    2013-08-15 22:32:22.000000000 -0700
+++ vmhgfs-only.patched/inode.c    2013-09-16 21:31:12.323041668 -0700
@@ -31,6 +31,9 @@
 #include <linux/namei.h>
 #endif
 #include <linux/highmem.h>
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 11, 0)
+#include <linux/dcache.h>
+#endif

 #include "compat_cred.h"
 #include "compat_fs.h"
@@ -1890,7 +1893,11 @@
 #endif
                            &inode->i_dentry,
                            d_alias) {
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 11, 0)
+         int dcount = d_count(dentry);
+#else
          int dcount = dentry->d_count;
+#endif
          if (dcount) {
             LOG(4, ("Found %s %d \n", dentry->d_name.name, dcount));
             return HgfsAccessInt(dentry, mask & (MAY_READ | MAY_WRITE | MAY_EXEC));
@@ -1943,10 +1950,12 @@
       list_for_each(pos, &inode->i_dentry) {
          int dcount;
          struct dentry *dentry = list_entry(pos, struct dentry, d_alias);
-#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 38)
-         dcount = atomic_read(&dentry->d_count);
-#else
+#if LINUX_VERSION_CODE >= KERNEL_VERSION(3, 11, 0)
+         dcount = d_count(dentry);
+#elif LINUX_VERSION_CODE >= KERNEL_VERSION(2, 6, 38)
          dcount = dentry->d_count;
+#else
+         dcount = atomic_read(&dentry->d_count);
 #endif
          if (dcount) {
             LOG(4, ("Found %s %d \n", (dentry)->d_name.name, dcount));

```
4. Do a 
    cd $home/Desktop
    sudo ./fix.sh
and answer the questions then reboot.

5. Folder sharing "should" work now.

acknowledgement:
[http://translate.google.com/translate?hl=en&sl=ja&u=http://www.gembook.org/install_vmware_tools_ubuntu_1310.html&prev=/search%3Fq%3Dubuntu%2B13.10%2B%25E2%2580%2598struct%2Bdentry%25E2%2580%2599%2Bhas%2Bno%2Bmember%2Bnamed%2B%25E2%2580%2598d_count%25E2%2580%2599%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26biw%3D1600%26bih%3D729](http://translate.google.com/translate?hl=en&sl=ja&u=http://www.gembook.org/install_vmware_tools_ubuntu_1310.html&prev=/search%3Fq%3Dubuntu%2B13.10%2B%25E2%2580%2598struct%2Bdentry%25E2%2580%2599%2Bhas%2Bno%2Bmember%2Bnamed%2B%25E2%2580%2598d_count%25E2%2580%2599%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26biw%3D1600%26bih%3D729)

---

