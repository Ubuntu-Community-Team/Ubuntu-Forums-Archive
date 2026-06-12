---
title: "VSFTPD chroot_local_user problem - an unexpected TLS packet was received"
date: 2017-06-17
forum: Server Platforms
---

### Post by ripeart on 2017-06-17
In vsfptd.conf when I comment out #chroot_local_user=YES then I can connect over Filezilla just fine however the output displays the entire path


/
-media
--ftproot
---mmg
----root


What I am trying to get it to do is when user 'mmg' logs in display only the "root" folder that lives inside "mmg"


In vsftpd.conf have the following option set:

```

local_root=/media/ftproot/mmg/root

```


and permissions on that folder are as follows:

```

root@server:~# ls -la /media/ftproot/mmg/root/
total 16
drwxr-xr-x 2 mmg    mmg     4096 Jun 17 22:25 .
dr-xr-xr-x 3 nobody nogroup 4096 Jun 17 21:59 ..
-rw-r--r-- 1 root   root       9 Jun 17 22:02 test.txt
-rw------- 1 mmg    mmg        9 Jun 17 22:20 upload.txt

```


Any help is appreciated!

---

