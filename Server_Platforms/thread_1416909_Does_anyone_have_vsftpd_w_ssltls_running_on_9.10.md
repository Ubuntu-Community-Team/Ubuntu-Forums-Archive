---
title: "Does anyone have vsftpd w/ ssl/tls running on 9.10?"
date: 2010-02-26
forum: Server Platforms
---

### Post by Jive Turkey on 2010-02-26
I have been futzing around with this for longer than any reasonable person would.  If you have this working could you please post how you got it.  No matter what I do I get no feedback in /var/log/vsftpd.log to help.

Here is my vsftpd.conf```
listen=YES
background=YES
listen_ipv6=no
delete_failed_uploads=YES
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
listen_port=990
force_dot_files=YES
pasv_enable=NO
anonymous_enable=no
local_enable=YES
write_enable=YES
local_umask=022
anon_upload_enable=NO
anon_mkdir_write_enable=NO
dirmessage_enable=YES
use_localtime=YES
hide_ids=YES
xferlog_enable=YES
#connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
idle_session_timeout=600
data_connection_timeout=120
nopriv_user=nobody
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
ftpd_banner=Welcome to node1 FTP service.
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=NO
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd_cert.pem
debug_ssl=YES

```
again nothing gets posted in any log anywhere with regard to vsftpd even though it is running.  I think something fails with regard to TLS initialization as filezilla gives me this:```

Status:	Connection established, initializing TLS...
Error:	Connection timed out
Error:	Could not connect to server
```
I have a self signed certificate in /etc/ssl/certs/vsftpd_cert.pem 

If anyone has this working could you please advise me on a working conf, and possibly how you created the certificate.

I'm using v 2.2.0 from the repositories on a pretty fresh install of 9.10 server(less than 24hrs old).

---

### Post by Jive Turkey on 2010-02-26
After a fair amount of trial and error and the subsequent loss of 10-20% of the hair on the top of my head I believe I have found a serious security issue.  I will not detail the issue here.

Can anyone tell me what this issue means and what I should do to resolve it, if anything?
```
(Reading database ... 61281 files and directories currently installed.)
Unpacking vsftpd (from .../vsftpd_2.2.0-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up vsftpd (2.2.0-1ubuntu1) ...
vsftpd user (ftp) already exists, doing nothing.
[COLOR="Red"]update-rc.d: warning: vsftpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)[/COLOR]

```This is after doing sudo apt-get purge vsftpd and reinstalling it.

---

### Post by Jive Turkey on 2010-02-27
After filing a bug, and doing some more investigation I believe the vsftpd package is unusable and possibly a malicious threat as it exists in the repositories currently, at least for 9.10.

---

### Post by hessiess on 2010-02-27
Use SFTP (SSH) instead. The design of the FTP protocol means that its next to imposable to encrypt it and actually have it work at the same time.

---

### Post by Ntr0s on 2010-03-30
Yes, I've been using vsftpd with TLS encryption on 9.10 x64 for a while now, no problems what so ever.  I love it.  Utterly stable.

Here is my vsftpd config file:

# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#listen_port
listen_port=340
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
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
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
idle_session_timeout=500

#connection_timeout
connect_timeout=2500
# You may change the default value for timing out a data connection.
data_connection_timeout=2500
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=In Nomeni Patri Et Fili Spiritus Sancti.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES

#tpc_wrappers
tcp_wrappers=NO

#pasv_enable
pasv_enable=YES
pasv_min_port=6500
pasv_max_port=6550

#real time data
setproctitle_enable=YES

#Rates
#anon_max_rate=0
local_max_rate=404800

#Client connection limit
max_clients=10
max_per_ip=4

#FTP Root Files
anon_root=/var/ftp
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
#rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
#rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

#SSL/TLS Configuration
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=YES

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

rsa_cert_file=/etc/pki/tls/certs/vsftpd.pem

---

### Post by Ntr0s on 2010-03-30
Oh yeah, I used these series of instructions to configure vsftpd: 
[http://www.brennan.id.au/14-FTP_Server.html](http://www.brennan.id.au/14-FTP_Server.html)

Also, from the vsftpd home page [https://calomel.org/vsftpd.html](https://calomel.org/vsftpd.html)  there is this great sh script that runs from the command line called vsftpd_watcher.sh  It shows which user is logged in, bandwidth, file downloading or uploading, etc.  

Also using EtherApe that displays a nice visual map of who is (IP address of user) connected to my server.  Its a decent setup, so Etherape running with a transparent console running vsftpd_watcher. 

I'm also running a tail on the vsfptd log file to view additional info.  "sudo tail -f /var/log/vsftpd.log

Anyway, save this script as .sh

#!/bin/sh
#
## Calomel.org VsFTPd Watcher -- vsftpd_watcher.sh
#
while [ 1 ]
  do
    clear
    echo "  Calomel.org VsFTPd watcher                      `date`"
    echo ""
    ps -C vsftpd -o user,pid,stime,cmd
    echo ""
  # echo "----total-cpu-usage---- -dsk/total- -net/total- ---paging-- ---system--"
  # echo "usr sys idl wai hiq siq| read  writ| recv  send|  in   out | int   csw "
    dstat 1 5
done

---

