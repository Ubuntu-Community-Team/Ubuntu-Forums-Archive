---
title: "Can't access ftp server via browsers"
date: 2011-04-03
forum: Server Platforms
---

### Post by salu on 2011-04-03
Pls help!
 
I installed vsftp on ubuntu10.04.2 32-bit server. I can access ftp remotely by using ftp client tool -- Filezilla, but can't access ftp site from web browsers (tried on both IE8 & Firefox). when type [ftp://xxx.xxxx.xxx](ftp://xxx.xxxx.xxx), the browser has no response. 
 
How to solve the issue? Thanks in advance!

---

### Post by NedHanlon on 2011-04-03
Why don't you post your vsftpd configuration file. That would help.
     Things that might be wrong.
[INDENT]Atypical port usage. [/INDENT]
[INDENT]User permissions.[/INDENT]
[INDENT]IE also takes you directly to / which vsftpd may not allow. [/INDENT]

---

### Post by salu on 2011-04-03
# config file /etc/vsftpd.conf
#
listen=YES
#
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
#
#anon_upload_enable=YES
#
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
use_localtime=YES
#
xferlog_enable=YES
#
connect_from_port_20=YES
#
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
#async_abor_enable=YES
#
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
chroot_local_user=YES
#
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
#ls_recurse_enable=YES
#
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default. These settings are more Debian-friendly.
#
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem

---

