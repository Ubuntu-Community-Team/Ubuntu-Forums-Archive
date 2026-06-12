---
title: "VSFTPD: Can't Change Home Directory to a Seperate Partition"
date: 2008-04-03
forum: Server Platforms
---

### Post by azurepancake on 2008-04-03
I've recently set up VSFTPD on this system and it works great when its home directory is set in the partition which it is installed under, but when I attempt to configure it for a directory on the partition where I keep all my media, I get the following problem:

tristan@tux:~$ ftp localhost
Connected to localhost.
220 (vsFTPd 2.0.5)
Name (localhost:tristan): anonymous
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
226 Transfer done (but failed to open directory).

I can't get a list of the directory and cannot access any of the files in that directory. Here is my VSFTPD.conf file in its entirety, without the commentary.:

listen=YES
#listen_ipv6=YES
anon_root=/media/sda5
#local_enable=YES
#write_enable=YES
#local_umask=022
#anon_upload_enable=YES
#anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

Any one have a idea on the solution to my problem? Any advice would be much appreciated. Thanks.

---

### Post by azurepancake on 2008-04-04
I'm still have trouble with changing VSFTPD's home directory. Any one have an idea about what I should do?

---

### Post by azurepancake on 2008-04-04
Hm, I am not sure how factual this is, but after doing a little reading I've came to the realization that VSFTPD might not support NTFS partitions.

I made a little EXT3 partition to test it out and VSFTPD can indeed use it as it's home.

OH well!

---

