---
title: "FTP, Apache, and Permissions"
date: 2007-01-12
forum: Server Platforms
---

### Post by kramerkeller on 2007-01-12
I posted something on this ealier and did not recieve a reply.  I have studied up and now think I have a better understanding, but still need some help.

I have created a group ftp-users and I want to make it so that every time that user adds a file the associated files are written with read and execute access to all users.

I know how to go in and do this with chmod, but when I ftp into the server with web files I would like those files to be written as read and executable to all users without having to go in after uploading the files and chmod.

---

### Post by Brazen on 2007-01-12
You won't do this through the ftp configuration.  You'll do this through the file system.  Damn, for the life of me know I can't think of what the command is, but you can set default permissions on a directory to be applied to files created in that directory.

You'll want your default mode to be set to 755 to accomplish this.  If I think of the command, I'll post it.

edit:  "umask" that's what it is.  I believe the command you want to use is:```
umask 755 /path/to/ftp/folder
```

---

### Post by kramerkeller on 2007-01-16
That was it thanks!

---

### Post by Brazen on 2007-01-16
You're welcome.  Glad I helped!

---

