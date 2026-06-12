---
title: "Anonymous NFS access"
date: 2010-10-01
forum: Server Platforms
---

### Post by Trollslayer on 2010-10-01
OK, this is an unusual request.
I have some embedded systems that need to write files to a NFS share but the embedded systems only have 'root' without a password so is there any way to set up a NFS share that can be accessed anonymously?
Thanks.

---

### Post by nr1c0re on 2010-10-03
may be I ask something wrong... but where have you found nfs authentication?

check [http://manpages.ubuntu.com/manpages/maverick/en/man5/exports.5.html](http://manpages.ubuntu.com/manpages/maverick/en/man5/exports.5.html)

like
/pub            *(rw,insecure,all_squash)

should work for you

---

