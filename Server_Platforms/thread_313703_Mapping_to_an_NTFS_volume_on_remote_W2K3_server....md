---
title: "Mapping to an NTFS volume on remote W2K3 server...."
date: 2006-12-06
forum: Server Platforms
---

### Post by bhathco on 2006-12-06
I'm runner a 6.06 server, that'll be used as an ftp server.  I found out that our backup solution does not support Ubuntu, or any other Debian based distro. So, I was wondering if I could mount a remote ntfs volume and rsync to that locally mapped resource. if this is possible, what would be my best approach. Also, what might be other options, besides locally attached tape drive.

Thanks!

---

### Post by elst on 2006-12-06
Linux can mount Windows file shares, and the Samba command-line software works very well. It actually talks to the Windows server using the CIFS protocol that Windows clients use - the fact that the volume is NTFS formatted doesn't matter here. You can definitely write a script that mounts a Windows shares and copies files across.

If your backup solution doesn't support Debian agents then this is probably the best approach - aother method would be to configure IIS WebDAV or FTP to allow your Linux system to upload to Windows with one of those protocols. You could easily use a local tape drive with tar, Amanda, or Bacula, but it's probably better to centralise backups if you can.

---

