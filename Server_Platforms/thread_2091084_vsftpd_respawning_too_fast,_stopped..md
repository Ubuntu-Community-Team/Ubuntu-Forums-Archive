---
title: "vsftpd: respawning too fast, stopped."
date: 2012-12-04
forum: Server Platforms
---

### Post by b1sh0p on 2012-12-04
hi all,

I have read several posts about this problem but with no solution for my problem.
version: vsftpd (2.3.5-1ubuntu2) 

conf.
```
listen=YES
anonymous_enable=NO
port_enable=YES

local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
data_connection_timeout=620
nopriv_user=nobody
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=NO

rsa_cert_file=/etc/vsftpd/vsftpd.pem
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

```

and erro when i start

```
[6046487.300645] init: vsftpd main process ended, respawning
[6046487.309673] init: vsftpd main process (3099) terminated with status 1
[6046487.309711] init: vsftpd respawning too fast, stopped

```
i generate cert on path

thx in advance

---

### Post by b1sh0p on 2012-12-09
i try ssl things and default config and same error, anyone can help plz...im already read 6 topics here and a lot topics on google and dont have any solution yet

---

