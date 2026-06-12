---
title: "Permission Denied dumping master file"
date: 2011-03-21
forum: Server Platforms
---

### Post by Revo99 on 2011-03-21
Hello All,

Thank you all for your help in advance. I am attempting to setup an Ubuntu server as a secondary DNS server. It seems whenever it tries to dump the master file the system log shows Permission denied. 

Any help would be appreciated. Please let me know if more information is needed.

NOTE: where it says example.com I have simply removed my actual Domain name. 


Mar 21 21:49:24 ulinux named[14418]: zone example.com/IN: Transfer started.
Mar 21 21:49:24 ulinux named[14418]: transfer of 'example.com/IN' from 192.168.0.15#53: connecte$
Mar 21 21:49:24 ulinux named[14418]: zone example.com/IN: transferred serial 2011032100
Mar 21 21:49:24 ulinux named[14418]: transfer of 'example.com/IN' from 192.168.0.15#53: Transfer$
Mar 21 21:49:24 ulinux named[14418]: dumping master file: tmp-fTlD2K2QST: open: permission denied
Mar 21 21:49:24 ulinux named[14418]: zone 0.168.192.in-addr.arpa/IN: Transfer started.
Mar 21 21:49:24 ulinux named[14418]: transfer of '0.168.192.in-addr.arpa/IN' from 192.168.0.15#53: $
Mar 21 21:49:24 ulinux named[14418]: zone 0.168.192.in-addr.arpa/IN: transferred serial 2011032100
Mar 21 21:49:24 ulinux named[14418]: transfer of '0.168.192.in-addr.arpa/IN' from 192.168.0.15#53: $
Mar 21 21:49:24 ulinux named[14418]: dumping master file: tmp-3hPkoCVeyc: open: permission denied

Cheers,

Revo

Using Ubuntu Server 10.10

---

### Post by SeijiSensei on 2011-03-21
> **Revo99 said:**
> Thank you all for your help in advance. I am attempting to setup an Ubuntu server as a secondary DNS server. It seems whenever it tries to dump the master file the system log shows Permission denied.

There are two possible problems.  First, make sure that the secondary is listed in the "allow-transfer" directive in the primary's named.conf file.  In addition, if the nameserver is running in a chroot environment, all the files and directories in that environment must be owned by the same user named runs as -- "bind" in Debian/Ubuntu; "named" in RHEL/CentOS.

---

