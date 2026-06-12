---
title: "VSFTPD - multiple virtual users assigned to alternate local roots??"
date: 2012-07-23
forum: Server Platforms
---

### Post by wimnms on 2012-07-23
Hello,

*vsftpd* 

This is about VIRTUAL not real OS users.

Is this (below) even possible?

/mnt/iofiles/FA <--  3 virtual users assigned to this directory upon login
/mnt/iofiles/AD <--- 5 virtual users assigned to this directory upon login
/mnt/iofiles/HR <--- 7 virtual users assigned to this directory upon login
. . .
/mnt/iofiles/??  <--- x virtual users assigned to this directory upon login

I want individual VIRTUAL accounts (no group accounts) to be mapped to the same directory.  This would be departmental.  Financial Aid people would all have individual accounts and would need to upload/download to the FA directory.  They cannot move up to /mnt/iofiles.  This would also be the case for AD (Admissions), HR (Human Resources), etc.

The box administrator has said NO O.S. accounts so we can only use virtual.  AND we can only use vsftpd.  (Or else I would have gone with ProFTPD or PureFTPD which I am more familiar with.)

Anyone have ideas?

I tried to override using user_config_dir and placing an indvidual account named file with local_root=/mnt/iofiles/FA for someone but it doesn't work.

** snippet from vsftpd.conf **
guest_enable=YES
guest_username=ftpvuser
virtual_use_local_privs=YES
user_config_dir=/opt/vsftpd/vsftpd_users

** /opt/vsftpd/vsftpd_users/test file **
local_root=/mnt/iofiles/FA

Thanks much!!!!

P.S.  When is the user_config_dir info read?  Is that dynamic?  Or how would I be sure it is being used?

---

### Post by wimnms on 2012-07-23
This is a follow-up.

For anyone else stuck like this....

I was working under a non-root account.

I *believe* I got it fixed.

All files within the user_config_dir are now *OWNED* by root.

Before that, I believe they were ignored.

Continuing to test this theory!!!  8)

---

