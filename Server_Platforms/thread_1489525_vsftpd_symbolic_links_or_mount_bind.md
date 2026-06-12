---
title: "vsftpd: symbolic links or mount bind?"
date: 2010-05-21
forum: Server Platforms
---

### Post by apeganz on 2010-05-21
Hello everyone,

I'm setting up an ftp server with lucid server. A lot of the folders that should be accessible via the ftp are in different directories (and can't be moved without a LOT of hazzle) and I have to either symlink or mount bind them to the ftp chroot dir.
Now I'm wondering which one is the saver variant?
My guess is mount bind, but I'm not that familiar with the internal workings of linux and vsftpd (plus for symlinks I wouldn't have to change/create any scripts, just create them once...), so please help O:)

Best wishes,
Alex

---

### Post by cdenley on 2010-05-21
If the user is chroot'ed to a directory, you cannot create symlinks for them to allow access outside that directory. You would have to use a mount bind.

---

