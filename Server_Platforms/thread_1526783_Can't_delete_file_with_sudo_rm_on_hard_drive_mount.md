---
title: "Can't delete file with sudo rm on hard drive mounted via usb"
date: 2010-07-08
forum: Server Platforms
---

### Post by lpanebr on 2010-07-08
Hello,

I have a hard drive mounted via usb that I use for backup via rsync. Some folders in this HD have 49:49 for owner:group and on these folders I am unable to delete files even with "sudo rm" or "sudo rm -rf". Here's the error for one file:

```
lpanebr@svn-server:~$ sudo rm -rf /media/backupexterno/backup/serverip4/tmp/crossbrowser_br.js
[sudo] password for lpanebr: 
rm: cannot remove `/media/backupexterno/backup/serverip4/tmp/crossbrowser_br.js': Read-only file system
lpanebr@svn-server:~$
```

In all other folders I can remove files normally and I have no idea why these folders got this weird owner:group...

Please help. thanks.

Luciano

---

