---
title: "FTP Server Default Permission Issues"
date: 2011-08-29
forum: Security
---

### Post by MicahInNY on 2011-08-29
Hi Everybody;

I am having an issue with an FTP server.  I crated an "FTPAdmin" account and an "FTPuser" account as well as an "FTPUsers" group and added both account to that group.  I created an FTP folder and made the owner the Admin account and also added it to that group.  I gave the folder 750 permissions so only the Admin can upload or delete anything.  Both accounts can connect the the server via FTP a client and seem to be behaving properly.

The problem I am having is that all the files that the Admin uploads to the server are defaulting to 600 permission and the User account can't even see the files.  I can manually change the permissions, but how can I change what the default permissions are?  I checked the umask in /etc/permissions and it is set to 022.  If I understand correctly, that should just take away write permissions for User and Other, so I don't think that's the problem.

Any advice would be greatly appreciated.

Micah

---

### Post by Bachstelze on 2011-08-29
I suspect you are using vsftpd. Change local_umask in vsftpd.conf to 022 instead of the default 077.

---

### Post by MicahInNY on 2011-08-30
Thanks a lot for that, that did the trick! 

Micah

---

