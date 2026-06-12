---
title: "Automagically copy files across network?"
date: 2008-05-28
forum: Server Platforms
---

### Post by monstermudder78 on 2008-05-28
Here is the setup: One computer called ubuntuserver.  One computer called desktop.  Both are running ubuntu 8.04.  What I want to do is copy opt/foldingathome/1/unitinfo.txt (on desktop) to /var/www/unitinfoDesktop.txt (on ubuntuserver) every hour or so, allowing an HTML file in /var/www/ to link to the file.  I used cron to set up an automatic copy on ubuntuserver, but I can't get cron to copy across the network using scp or cp, I am guessing due to password issues.  If this problem makes sense to anyone could you point me in the right direction please?

---

### Post by heebus on 2008-05-28
Look into running rsync over ssh in a simple script.  You can add that script to cron.  This article is perfect for what you want.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

---

### Post by monstermudder78 on 2008-05-28
> **heebus said:**
> Look into running rsync over ssh in a simple script.  You can add that script to cron.  This article is perfect for what you want.

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

Cool, thanks.  I am looking into it now.

---

### Post by hyper_ch on 2008-05-29
or use SSHFS/NFS and mount the remote server into your local file system and then copy the files over.

---

