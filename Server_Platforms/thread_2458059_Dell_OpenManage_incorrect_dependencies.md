---
title: "Dell OpenManage incorrect dependencies"
date: 2021-02-15
forum: Server Platforms
---

### Post by jamesmhowe on 2021-02-15
The latest OpenManage repos are built for the wrong dependencies.
[https://linux.dell.com/repo/community/openmanage/](https://linux.dell.com/repo/community/openmanage/)

Installed srvadmin-storageservices-cli v9.5.0 from the Focal repo.
On running, get the message:
 
  omhelp: error while loading shared libraries: libxslt.so.1: cannot open shared object file: No such file or directory

As far as I can see, Ubuntu has been shipping libxslt1.1, not 1, for years.

---

### Post by deadflowr on 2021-02-15
libxslt.so.1 is part of the libxslt1.1 package.
The file should be located at /usr/lib/x86_64-linux-gnu/libxslt.so.1
That file is a link to another file which on focal should be /usr/lib/x86_64-linux-gnu/libxslt.so.1.1.34.

Either check if the link is broken or create it or just reinstall the package.
If none of that works you'll probably need to contact dell : [https://lists.us.dell.com/mailman/listinfo/linux-poweredge]("https://lists.us.dell.com/mailman/listinfo/linux-poweredge")

---

