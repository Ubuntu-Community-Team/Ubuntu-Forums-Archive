---
title: "Make FTP server overwrite symlinks with files"
date: 2009-12-19
forum: Server Platforms
---

### Post by joelwhitehouse on 2009-12-19
I want to make an ftp server directory that is COMPLETELY readable/writable to the users.  However, I'd also like to use symlinks to point to certain files that I don't want to be modified.

So when a user tries to download a file, I want the FTP server to follow the symlink and retrieve that file.  But when a user tries to upload another file of the same name, I want the symlink to be replaced with the new file.  I don't want the referent of the symlink to be overwritten!

This way a user can completely overwrite any data in this directory without actually destroying any of the initial symlinked data that I provide to them.

How can I implement this behavior?

Thanks!

---

