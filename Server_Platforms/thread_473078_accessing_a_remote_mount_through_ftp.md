---
title: "accessing a remote mount through ftp"
date: 2007-06-13
forum: Server Platforms
---

### Post by Brazen on 2007-06-13
We have an vsftp server and we have a Samba file server.  There is a 300 Gig folder on our file server that we would like to make accessible via ftp, but our exisiting ftp server does not have nearly that much space.  So, I was hoping to mount the file share on the ftp server and then use "mount --bind" to create mount points in each of the users home directories that need access to the files.

Unfortunately, this doesn't work.  I can see the files from the ftp client, but if I try to download a file, it just times out and keeps retrying.  I've also tried cifs to mount the remote share and it does the same thing.

Does anybody know of a way to get this to work?

---

