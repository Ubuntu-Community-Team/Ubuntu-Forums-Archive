---
title: "FTP ip based accounts"
date: 2008-03-25
forum: Server Platforms
---

### Post by xzased on 2008-03-25
Is there a way to setup user accounts so that a user can only download documents from a specific computer or network? Kinda ip restricted accounts? Is there something similar around? Thanks :)

---

### Post by Mr. C. on 2008-03-25
Yes.

For example, vsftpd with tcpwrappers can be used together to support IP-based configurations. The connecting IP address dictates which configuration file is used, and further restrictions can be user-based as well.  There are lots of combinations.

Other FTP servers do likewise.

What do you have setup thus far?

---

### Post by xzased on 2008-03-26
Thanks Mr. C, you have pointed me in the right direction. I have nothing so far, just wondered if such thing was possible haha. I'll start building that. ::guitar:

---

### Post by netlogic on 2008-03-27
It depends on what you want to do. You can also use multiple scripts for iptables to restrict which ftp servers a locked down machine can access using cron or one ftp servers can replicate scripts to other ftp servers using fail2ban and rsync with ssh. You can also configure your PAM than the default setting  that it was packaged. You can also use the data in your /var/log/vsftpd.log to restrict the ip after certain amount of downloads.

---

### Post by r0biwan on 2008-03-27
With [Pure-FTPd]("http://www.pureftpd.org") you can also configure accounts to only allow certain IP addresses.

---

### Post by netlogic on 2008-03-27
I prefer the iptable method, because you can control unnecessary usage with custom scripts and tc.

---

