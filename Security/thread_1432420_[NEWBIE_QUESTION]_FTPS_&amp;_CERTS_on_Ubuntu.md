---
title: "[NEWBIE QUESTION] FTPS &amp; CERTS on Ubuntu"
date: 2010-03-17
forum: Security
---

### Post by RushRepsaJ on 2010-03-17
Dear readers,

I tried today to make a FTPS server. But I coulnt find out. Here are the configs I made, what im doing wrong :(. I used these how-to's

[https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html](https://help.ubuntu.com/9.04/serverguide/C/ftp-server.html)
[https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html)

[QUOTE="/etc/vftpd.conf"]
listen=yes
anomyous_enable=yes
local_enable=yes
write_enable=yes
dirmessage_enable=yes
user_localtime=yes
xferlog_enable=yes
connect_from_port_20=yes
secure_chroot_dir=/var/run/vsftpd/empty
rsa_cert_file=/etc/ssl/certs/server.crt
rsa_private_key_file=/etc/ssl/private/server.key
ssl_enable=Yes
force_local_logins_ssl=YES
force-local_data_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
[/QUOTE]

The cert file and the private key are on the right spot. My vsftpd.log is empty. 

> root@ubuntu:/var/log# sudo /etc/init.d/vsftpd restart
 * Stopping FTP server: vsftpd
No /usr/sbin/vsftpd found running; none killed.
   ...done.
 * Starting FTP server: vsftpd
   ...done.
I can't reach my server with FileZilla (OS X). FileZilla says 'connection refused'. Does anyone know what I have missed ??

---

### Post by cdenley on 2010-03-18
VSFTPD uses explicit SSL, which uses port 21. Filezilla calls this FTPES. FTPS in filezilla means implicit SSL, which uses port 990. VSFTPD doesn't use implicit SSL by default, which means it doesn't listen on port 990. Connections to port 990 will be refused.

---

### Post by mfrizzi on 2010-05-16
Hello all,

I'm trying to use the require_cert=YES and ca_certs_file PATH TO CERT flags into vsftpd.conf

the configuration that I want to do is due to the fact that I want only workstations with certificate distribuited by me connecting to my vsftpd site.

below the complete configuration file: unfortunatly the last two line must be #-ed in order to VSFTPd to start.
my questions are:
- where (folder) do I have to put the certificate file?
- it's enought for me to create one client certificate with the command 'openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/ssl/private/clientvsftpd.pem -out /etc/ssl/private/clientvsftpd.pem' and distribute it to clients that I want to let connect to my ftps site?

Thank you in advance!

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=NO
anon_mkdir_write_enable=NO
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
idle_session_timeout=600
data_connection_timeout=120

#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#ascii_upload_enable=YES
#ascii_download_enable=YES
#

ftpd_banner=Welcome to blah FTP service.
chroot_local_user=YES
chroot_list_enable=NO
chroot_list_file=/etc/vsftpd.chroot_list
ls_recurse_enable=NO
#
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem

ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
listen_port=990
pasv_min_port=62100
pasv_max_port=62150
# require_cert=YES
# ca_certs_file /etc/ssl/private/clientvsftpd.pem

---

### Post by cdenley on 2010-05-17
Why post here? Client certificate authentication has nothing to do with this thread, and it already has its own thread.

---

### Post by mfrizzi on 2010-05-17
> **cdenley said:**
> Why post here? Client certificate authentication has nothing to do with this thread, and it already has its own thread.

I've searched for client cerificate authentication but i've never found the thread you're speaking about: could you pls point me on the right path?
thank you 
Manlio

---

### Post by cdenley on 2010-05-17
> **mfrizzi said:**
> I've searched for client cerificate authentication but i've never found the thread you're speaking about: could you pls point me on the right path?
thank you 
Manlio

You should already know the thread. You created it!

[http://ubuntuforums.org/showthread.php?t=1485015](http://ubuntuforums.org/showthread.php?t=1485015)

Duplicate posting is very annoying.

---

### Post by uRock on 2010-05-17
> **cdenley said:**
> You should already know the thread. You created it!

[http://ubuntuforums.org/showthread.php?t=1485015](http://ubuntuforums.org/showthread.php?t=1485015)

Duplicate posting is very annoying.
As Homer Simpson likes to say, "Doh!"

---

