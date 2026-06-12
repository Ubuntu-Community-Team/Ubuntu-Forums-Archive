---
title: "vsftpd user can't log in"
date: 2012-06-27
forum: Server Platforms
---

### Post by SacramentoRob on 2012-06-27
hi folks, 

I'm having trouble with vsftpd.  After years of flawless performance on my Edgy (6.10) platform, vsftpd hasn't worked right since I upgraded to Lucid (10.04) in January 2012.

sftp works fine.  ftp drops the following error and denies access:  Cannot connect to ftp://<IP>:bad login:  OOPS: config file not owned by correct user, or not a file

This is my config file (vsftpd.conf)
anonymous_enable=YES
anon_root=/home/ftp
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
ftpd_banner=Welcome to Uptown FTP service.
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
user_config_dir=/etc/vsftpd_user_conf
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
session_support=YES
listen=YES
<eof>

/var/log/vsftpd.log reports this:
Wed Jun 27 16:16:27 2012 [pid 3393] CONNECT: Client "IP"
Wed Jun 27 16:16:27 2012 [pid 3392] [Me] OK LOGIN: Client "IP"
<eof>

tcpdump reports plenty of traffic on ports 20 and 21, back and forth between the server and the accessor.

>lsof -i :21 reports:
COMMAND  PID USER   FD   TYPE   DEVICE SIZE/OFF NODE NAME
vsftpd     6752 root    3u  IPv4 12819833      0t0  TCP *:ftp (LISTEN)


>service vsftpd status reports:
vsftpd start/running, process 6752

/var/log/auth.log reports:
Jun 27 16:24:14 Server vsftpd: pam_unix(vsftpd:session): session opened for user Me by (uid=0)
Jun 27 16:24:14 Server vsftpd: pam_unix(vsftpd:session): session closed for user Me


I've been trying to fix this off and on for months.  I've read all the other posts that I can find that have similar problems--quite a few, actually--and I just can't get this thing working.  I think I've tried almost every permutation of file permissions possible.  It would be nice to know what file it can't access.

I'd appreciate any help. 

thanks in advance.

/Rob

---

### Post by SacramentoRob on 2012-07-21
::bump::

OK, I did some more experimenting on this.  The users actually can log in.  For some reason, they can't get any directory listings once they have logged in.

Is there a better place for this post?

Any help is appreciated.

Thanks, 
/Rob

---

