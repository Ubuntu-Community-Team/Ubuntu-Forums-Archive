---
title: "XFS, Samba, and ACL's"
date: 2005-11-14
forum: Server Platforms
---

### Post by grendelkhan on 2005-11-14
I am trying to set up Samba shares to have Windows style ACL's, rather than Unix style permissions.

I have enabled NT acl's in Samba, the shares are on an XFS partition, however I get no tab for permissions now on the Windows boxes.

Server is Breezy, using default Samba and XFS/libacl, clients are all XP SP2.

Any help anyone could give would be greatly appreciated!

---

### Post by BMWolf on 2007-11-20
I hate to resurrect an ancient thread, but I have nearly the same question. Clients are Vista. Biggest problem I'm experiencing is hidden files are no longer hidden after transfer, and when using robocopy all files are copied rather than just the changes. I'm kind of a noob, but I've searched and can't seem to find a solution.  I'm running Gutsy server, do I need a different kernel? The Samba share is located on a software raid 1 array, the rest on a separate ext3 drive. I've tried enabling ACL in samba, should I have to do anything else? Any help straightening this out would be greatly appreciated.

---

### Post by koenn on 2007-11-20
I'm not aware of built-in acl support in Samba, but you can add it by installing the package 'acl' (from universe). It enables posix-complient ACL's and is usually used for windows compatibility and active directory integration (i.e. use AD domain accounts to set file system security on shared files)
Maybe it's worth having a look at. 
Here are some notes :
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)

---

### Post by BMWolf on 2007-12-04
Thanks, I'll look into this and report back with my results.

---

