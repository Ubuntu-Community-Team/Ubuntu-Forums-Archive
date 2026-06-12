---
title: "Trouble with vsftpd server..."
date: 2010-06-17
forum: Server Platforms
---

### Post by username1000 on 2010-06-17
Hi ubuntus,

please help me... I have a webserver with vsftpd running. But unluckily the vsftpd service is down after one day. Here s my config:

listen=YES
listen_port=2121
anonymous_enable=NO
local_enable=YES
write_enable=YES
pasv_address=xxx.dyndns.org
pasv_addr_resolve=YES
pasv_enable=YES
pasv_min_port=1000
pasv_max_port=2120
anon_upload_enable=NO
anon_mkdir_write_enable=NO
local_root=/var/www
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=NO
# ftp_data_port=20000
ftpd_banner=Peters Data
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd





inux is1 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux
Ubuntu 10.04 LTS

Welcome to Ubuntu!
* Documentation: [https://help.ubuntu.com/]("http://www.ubuntu-forum.de/index.php?page=ExternalLink&url=https%3A%2F%2Fhelp.ubuntu.com%2F")

System information as of Tue Jun 15 09:03:35 CEST 2010

System load: 1.33 Memory usage: 8% Processes: 92
Usage of /: 5.2% of 35.00GB Swap usage: 0% Users logged in: 0

---

