---
title: "Trouble using iscsi on ubuntu server 9.10"
date: 2010-02-04
forum: Server Platforms
---

### Post by Dazzler-it on 2010-02-04
Hi to everybody, 
premises that use Ubuntu from little time and therefore I don't have a lot of experience on the system. I have installed for making a test the version 9.10 server and I have activated the access through iscsi to the disk of the same. I have also activated two clients (Ubuntu 9.10 Desk) that they access the same resource (always through iscsi). Now it happens to me that if from a client I create a new folder on the network disk, the other client doesn't see the folder nor the file. If I umount the network unit and I remount then the folder on the network disk it becomes visible, otherwise nothing. I have tried to look around for infos but without results. I hope that someone can give me some help to resolve the problem (if possible to resolve). It seems that the changes are not immediately syncronized.
Thank you.

---

### Post by kiranmurari on 2010-02-04
Hi,
       iSCSI is a block based protocol and not designed for concurrent access from multiple nodes. There are proprietary systems that allow this with a customized iSCSI stack but not with standard iSCSI.
   
Achieving concurrent access also depends on the filesystem type on the LUN (partition). In order to achieve concurrent access from multiple nodes - you need to have a clustered file system. Please see the below link for information on clustered filesystems
[http://www.enterprisestorageforum.com/sans/article.php/3834771](http://www.enterprisestorageforum.com/sans/article.php/3834771)

---

### Post by Xianath on 2010-02-04
If I am reading this correctly, you have multiple nodes mounting the same block device. In this case you want to use a clustered file system such as, but not limited to, OCFS2, GFS, VXFS etc. Otherwise one node will indeed not be aware from changes made from the other node. If you can't employ any of them, you'll have to rely on network file systems such as NFS of CIFS.

Regards,
Peter

---

### Post by Dazzler-it on 2010-02-12
Hi to all,
many thanks for your replies.
While waiting some replies, for my applications, I've just decided to try NFS and it seems to go.
When I'll have some time to spend,  I will try  the clustered file system solution as suggested.
So, many thanks to you, again.
See you.
Ninox. ;)

---

