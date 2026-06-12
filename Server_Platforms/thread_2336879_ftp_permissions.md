---
title: "ftp permissions"
date: 2016-09-12
forum: Server Platforms
---

### Post by Vegan on 2016-09-12
Once I had downloaded my log.tar.gz file I did not need it cluttering up my home folder so I tried to delete it with FileZilla

so what do I need to do now to get permissions fixed?

besides chmod 777 *

---

### Post by TheFu on 2016-09-12
Use ssh, login to the machine, and use "rm" to delete the file?  Is this a trick question?  
Or ... use sftp, just check that the sftp server isn't setup to prevent file deletions (not the default).  Could the plain ftp server be configured to prevent file deletions?

BTW, the permissions on the actual file ARE NOT used when trying to remove it. The directory permissions that hold the file are important. Check those.

---

### Post by Vegan on 2016-09-12
I can remove the file with Putty but not with FileZilla, is there some setting I have overlooked?

Eventually I will want to upload files to the LAMP box

---

