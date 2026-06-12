---
title: "Vsftpd ignoring pam_service_name"
date: 2011-03-03
forum: Server Platforms
---

### Post by MiniMeCZ on 2011-03-03
Hi,
I am having problem with setting vsftpd to authorise users from database.

I have tried two different ways:

/etc/pam.d/vsftpd
```
auth required /lib/security/pam_mysql.so user=FakaHedaUnix passwd=XXXXXX host=mysql.fakaheda.eu db=ftp table=ftp_accounts usercolumn=username passwdcolumn=password crypt=2
account required /lib/security/pam_mysql.so user=FakaHedaUnix passwd=XXXXXX host=mysql.fakaheda.eu db=ftp table=ftp_accounts usercolumn=username passwdcolumn=password crypt=2

```/etc/pam.d/ftp
```
auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
```But it doesnt matter what i set in /etc/vsftpd/vsftpd.conf
pam_service_name=ftp
or
pam_service_name=vsftpd
it can authorise only system users.

Does pam_service_name depends on another config value?

I am starting vsftpd by command:
```
vsftpd /etc/vsftpd/vsftpd.conf
```other settings in /etc/vsftpd/vsftpd.conf are applied corectly.

System is Ubuntu 10.04.2 LTS,
Vsftpd 2.3.4 - compiled and instaled
libpam-mysql 0.7 RC1 4build1 instaled by aptitude

Sorry for my english and thanks for any help.

---

