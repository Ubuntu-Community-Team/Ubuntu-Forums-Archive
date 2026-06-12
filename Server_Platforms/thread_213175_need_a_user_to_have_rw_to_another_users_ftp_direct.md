---
title: "need a user to have rw to another users ftp directory"
date: 2006-07-10
forum: Server Platforms
---

### Post by nephish on 2006-07-10
hello there,
i have an app that gets data via small files dropped into an ftp users home directory.
i set the ftp users home directory as /var/ftpData
that is the only purpose of this user account on the system, to upload the little data files and write them there. Now, my application runs as a different user that collects the ftp'd files, updates a database, then deletes the files. So, how can i set this up to where the data application user has permission to read and delete those files. I am using vsftpd on debian linux.

i am not opposed to using an anonomous user, but it has to be password protected.

thanks for any tips.

---

