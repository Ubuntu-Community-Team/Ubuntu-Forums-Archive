---
title: "vsftpd anonymous (500 OOPS: cannot change directory:ftp 500 OOPS: priv_sock_get_cmd)"
date: 2014-01-28
forum: Server Platforms
---

### Post by PanesaB on 2014-01-28
I am currently getting error msg
500 OOPS: cannot change directory:ftp 
500 OOPS: priv_sock_get_cmd
my vsftpd.conf looks like this

ftpd_banner= TFL FTP (10.30.0.13)
listen=YES
listen_port=21
connect_from_port_20=YES
local_enable=NO
download_enable=YES
write_enable=YES


xferlog_enable=YES
xferlog_file=/var/log/vsftpd.log


anonymous_enable=YES
anon_world_readable_only=NO
anon_upload_enable=YES
anon_root=/media/srv/ftp
anon_max_rate=50

and I've also had issues downloading and uploading im using ufw and currently have it disabled while im figuring this out but my usuall settings are
To                         Action      From
--                         ------      ----
20                         ALLOW       Anywhere
21                         ALLOW       Anywhere
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
1022                       ALLOW       Anywhere

any help would be gladly apreciated
-Bennett

---

