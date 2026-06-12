---
title: "FTP nested home folders"
date: 2007-09-24
forum: Server Platforms
---

### Post by vortmax on 2007-09-24
This will probably be a simple issue to resolve, but I'm having no luck.

I have an ftp server (proftpd) that I am using to host software updates on my network.  I need to have this folder read only accessible through anonymous ftp.  

Simple....

I also need to be able to add new updates to this folder via FTP, so I need a second privileged user who has wrx rights to the folder and can do so via ftp.  It would also be best if that 'updates' directory resided in the privileged user's main ftp directory.  The idea being that he can upload files to the server and then only place ones in the public folder that are ready to be distributed.

I've been fighting proftpd for a while with no success.  Any tips?

---

### Post by elst on 2007-09-25
For read-only access, straight HTTP is easier to work with than FTP. I'd suggest installing a Web server, and configuring it to offer up a directory. Set the permissions on that directory to give your account read-write access, and you can then upload stuff with SSH (SFTP). Apache is fine, lighttpd is better.

Generally, these days you shouldn't use FTP unless you have a specialized requirement that forces the issue - HTTP and SSH have largely superseded FTP.

---

### Post by Brazen on 2007-09-25
If I'm understanding this correctly, it sounds like you want to do a mount bind.

I just googled and glanced at this document, but it looks like it gives a desent explanation of the command and how to use it: [http://aplawrence.com/Linux/mount_bind.html](http://aplawrence.com/Linux/mount_bind.html)

---

