---
title: "Root-Like Rights in chroot Jail"
date: 2007-07-05
forum: Server Platforms
---

### Post by mojorising on 2007-07-05
Hi! I have an SFTP server set up with vsftpd over ssh. 

There is one jail with all my FTP users in it. Each user's directory has rights of 700 so they can only see their own files. I want to have one user that is not the root user who can access all the other jailed directories to get and delete files when necessary. 

Can anyone tell me how I can grant a user such privileges or where I can look for information on it? I've googled around quite a bit and checked these forums but no dice. 

Thank you!

Mike

---

### Post by ubuntu.daemon on 2007-07-05
Are you talking about like access to others files/accounts through terminal, or are you talking about with your native file browser?

---

### Post by Mr. C. on 2007-07-05
You haven't mentioned if these are local or virtual users.

Setup your unprivileged ftp users in one group, for example npgroup.
Setup your privileged ftp users in a different group, say pgroup.

For the unprivileged ftp users, make their files/directories group-owned by pgroup, permissions 770 (directories) and 660 (files).  And place your privileged users in group pgroup also.  This allows the privileged users to modify (via group privileges) the files/directories of your unprivileged users, but not the other way around (since they are in group npgroup, they will not have access via group permissions).

Be sure to set the appropriate *_umask setting in vsftpd.conf, and setup the privilege user's home directory to be the parent directory of all the non-privileged users.

Just as a clarification, 700 permissions are read, write, examine (not read-only as implied by your "can only see").

MrC

---

