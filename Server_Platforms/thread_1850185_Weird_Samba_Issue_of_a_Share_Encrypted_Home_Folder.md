---
title: "Weird Samba Issue of a Share Encrypted Home Folder"
date: 2011-09-26
forum: Server Platforms
---

### Post by markp_2000 on 2011-09-26
I'm having a very weird issue with Samba and my iMac.  I can only see my home directory share when I ssh into the box.  All other shares work fine.

I'm thinking the encrypt-fs only works when logged in as a user.  But that is just a guess.

Anyone have any ideas?

Mark

---

### Post by markp_2000 on 2011-09-26
OK - googling around I came up with this bug report.

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/838807](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/838807)

I ran this and it seemed to do the trick.  
```

mount.ecryptfs_private
```

---

