---
title: "VSFTPD Strange Activity"
date: 2006-01-29
forum: Server Platforms
---

### Post by valenciastud on 2006-01-29
VSFTPD works at blazing speeds across my local network, but file transfers go extremely slow when I connect over the net to my external ip address. 

I should also note that my Windows Serv-U ftp program works fine both locally and over the net, so I believe the problem is VSFTPD or Ubuntu specific.

I will post my config file below.

# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username

#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
#anon_root=/home/ftp/


anonymous_enable=NO
listen=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=kevin
ftpd_banner=Welcome to blah FTP service.
#secure_chroot_dir=/var/run/vsftpd
#pam_service_name=vsftpd
#rsa_cert_file=/etc/ssl/certs/vsftpd.pem



chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

---

