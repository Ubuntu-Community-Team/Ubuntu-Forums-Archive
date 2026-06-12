---
title: "SMB Buffer Size?"
date: 2011-09-22
forum: Server Platforms
---

### Post by pentas on 2011-09-22
Does anyone know if it is possible to create a ramdisk in linux (many GB) and then have samba use the ramdisk as a temporary buffer for large write operations to the drives to improve system performance?

This way, the client connecting to the server can move data quickly to the ramdisk while samba is flushing the buffer to disk.

---

### Post by zorglubx on 2011-09-23
Hey

I have thought about the same, and I know that /dev/shm is really what you need and is already implemented. On my server /dev/shm is 1007M (server has 2GB Ram), it would be lovely to be able to actually use this ramdisk.

I found a decent article on the subject here: [http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/](http://kevin.vanzonneveld.net/techblog/article/create_turbocharged_storage_using_tmpfs/)

I will check it out, and so could you ;)

Cheers

---

