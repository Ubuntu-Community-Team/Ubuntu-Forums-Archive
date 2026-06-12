---
title: "Accessing a Symbolic link to a directory via FTP"
date: 2006-04-03
forum: Server Platforms
---

### Post by wgregori on 2006-04-03
I'm working on a backup routine that uses TAR to pack up necessary directories after which an FTP client logs on to the system and moves the TAR file to another system.

My Problem is this:

I created a symbolic link in my HOME directory to my BACKUP directory.  I have no problem accessing the directory in the shell but when I ftp to the system the symbolic link to the directory does not allow me to access the linked directory.

I'm new to linux... is this the way it is suppose to work?  Can any give me suggestions for a work around?

Thanks,
Wayne Gregori

---

### Post by LordHunter317 on 2006-04-03
FTP is normally chrooted to your /home directory.  The eaisest solution is to copy the file there, or more ideally make a dedicated backup dump account.

---

### Post by wgregori on 2006-04-04
Thanks

---

