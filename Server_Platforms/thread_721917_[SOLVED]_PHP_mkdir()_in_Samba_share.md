---
title: "[SOLVED] PHP mkdir() in Samba share"
date: 2008-03-11
forum: Server Platforms
---

### Post by JimmyJam4PHP on 2008-03-11
I have a client that would like to use our application to browse and create/modify files and directories that are upload via ftp to a different server. Both servers are at the same location, so we have Samba installed on the FTP Server so that they can also use Windows Explorer to browse the files and use extra storage on the server. We have the directory used by the ftp users, "/home/ftp" shared with Samba and mounted on the web server at "/mnt/ftp".

Samba is setup to allow write access and "directory mask" is set to 775. However, when we create a directory on the share using mkdir(), the directory has 744 permissions. The folder on the share is owned by www-data:www-data, and the directory is mounted by www-data.

When we make directories through Windows Explorer or Nautilus in Ubuntu (which happens to be the web server), they are created with the proper permissions. Files created through our application are created with the proper permissions (664).

We spent several hours attempting to correct issue. Any help is greatly appreciated.

~ JimmyJam

---

### Post by JimmyJam4PHP on 2008-03-12
We just got this figured out.  We attempted to use chmod() in PHP and it appeared to work when looking at it through the share; however, when we looked at it directly on the server it had no effect.

In the end, we had to use "smbmount -d 775" to mount the directory on the web server.  Once we did this, everything worked perfectly.

---

