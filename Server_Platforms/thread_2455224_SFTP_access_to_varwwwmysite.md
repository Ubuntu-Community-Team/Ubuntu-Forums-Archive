---
title: "SFTP access to /var/www/mysite"
date: 2020-12-15
forum: Server Platforms
---

### Post by cgasser on 2020-12-15
Hello,

I do have some websites running un my Ubuntu 20. They are located under /var/www (/var/www/mysite1, /var/www/mysite2, etc.). To be able to upload files to the server I thought it is best to use SFTP. The SFTP server is basically working fine, but I'M strugling with the correct permission settings. For each site I have a dedicated FTP user stat is not allowed to loggon to the shell. A user like "ftpmysite1". These users are members of a group called "sftp".
The config in my ssh config gile looks like:

Match User ftpmysite1
ChrootDirectory /var/www/mysite1
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp

When doing so, I'm not able to connect to the server by SFTP. 

When changing the config to 
Match User ftpmysite1
ChrootDirectory /var/www
X11Forwarding no
AllowTcpForwarding no
ForceCommand internal-sftp


I am able to connect and also access the subfolder mysite1 . But I also can access all the other websites (which is no option).

Any idea what I'm doing wrong?

BR
Christoph

---

### Post by TheFu on 2020-12-15
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I wouldn't  allow uploading directly into web-server directories.  I wouldn't use sftp (or any Plain FTP) either.  I'd use rsync or git.  Website updates really should be handled by automation, so they are consistent and specialized steps like optimizing image files are included. Pulling the current website files using a crontab entry for the correct userid (probably www-data) would provide a systematic method for updates. Simply test for the existence of a file that gets removed whenever those files are copied into the website. Permissions management becomes easier that way.

An exact answer isn't possible without understanding the exact nature of the websites involved.  Static files can have much stricter permissions than that used by certain webapp systems.  I prefer to mount static file areas read-only for websites whenever possible. That solves many security problems. Just another thing to consider.

If you must use chroot and sftp, I'd drop the files into the HOME directory for each userid, but allow the www-data userid read access as needed.

---

