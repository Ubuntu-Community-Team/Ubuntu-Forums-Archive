---
title: "SFTP / SSH potential bug?"
date: 2012-06-13
forum: Server Platforms
---

### Post by H3110 on 2012-06-13
I've got a problem where to connect to a server via SFTP on 12.04 the chrooted directory can only be written to by root. But thus means the user cannot upload to it. SO changing the permissions so the user can write to it, ssh fails to authenticate :/.

---

### Post by CharlesA on 2012-06-13
How did you set up the chroot?

---

### Post by Lars Noodén on 2012-06-13
Keep the chrooted directory so that it can only be written by root and instead make a subdirectory (or more).  The subdirectories can then be owned by the user who can then write to them.

---

### Post by mxpxgx on 2012-09-04
I had the same problem and Lars' answer fixed it. Thanks a lot!

---

