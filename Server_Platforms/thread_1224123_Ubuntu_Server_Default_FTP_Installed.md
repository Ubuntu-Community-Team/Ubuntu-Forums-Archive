---
title: "Ubuntu Server: Default FTP Installed?"
date: 2009-07-27
forum: Server Platforms
---

### Post by Crath on 2009-07-27
So during installation of my fresh Ubuntu Server, I checked the "ftp" box. I was wondering where I could get info on what ftp software this is, where to set up accounts / remove default accounts, and make it point to just the web-server directories.  Thanks!

---

### Post by abarth on 2009-07-27
I believe that the default FTP server in ubuntu is vsftpd.
You can verify this by running in a terminal:

```
dpkg -l | fgrep ftpd
```

Here are some more information on how to configure vsftpd:

[https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)
[http://manpages.ubuntu.com/manpages/jaunty/en/man5/vsftpd.conf.5.html](http://manpages.ubuntu.com/manpages/jaunty/en/man5/vsftpd.conf.5.html)

For better security, consider to use sftp instead (from the package openssh-server).

Cheers,
Alex

---

