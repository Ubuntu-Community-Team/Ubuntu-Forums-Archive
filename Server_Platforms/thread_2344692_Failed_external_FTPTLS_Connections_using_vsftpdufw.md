---
title: "Failed external FTP/TLS Connections using vsftpd/ufw 14.04"
date: 2016-11-27
forum: Server Platforms
---

### Post by shelzmike2 on 2016-11-27
I have been banging my head for the past 2 days on this problem as I cannot seem to figure this out at all.

14.04 Server
UFW Enabled
using vsftpd
Explicit FTP over TLS
Works perfectly locally (using terminal FTP from RPi as well as Filezilla from Windows PC)

I am UNABLE to get any successful FTP connections using external IP OR hostname (using no-ip as a redirect, but this shouldn't matter as I get the same result as using direct IP).

Here are the various configs:

[B]vsftpd.conf
[/B]```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
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
#local_umask=022
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
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The# times returned by the MDTM FTP # command are also affected by this
# option.
use_localtime=YES
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
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
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
#ftpd_banner=Welcome to blah FTP service.
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
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
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
#
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
#
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH
#
# ADDED BY ME
user_sub_token=$USER
local_root=/home/$USER/ftp
#
#
#
pasv_min_port=40000
pasv_max_port=40050
#BELOW IS A MASKED URL, REMARKED HERE, BUT DOESN'T WORK EITHER WAY
#pasv_address=oh.domain.org
#pasv_addr_resolve=YES
#
#
#
userlist_enable=YES
userlist_file=/etc/vsftpd.userlist
userlist_deny=NO

```

**UFW **
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip


To                         Action      From
--                         ------      ----
22                         LIMIT IN    Anywhere
22/tcp                   ALLOW IN    Anywhere
1900/udp               ALLOW IN    Anywhere
8080:8082/tcp              ALLOW IN    Anywhere
20/tcp                     ALLOW IN    Anywhere
21/tcp                     ALLOW IN    Anywhere
40000:40050/tcp            ALLOW IN    Anywhere
22 (v6)                    LIMIT IN    Anywhere (v6)
22/tcp (v6)                ALLOW IN    Anywhere (v6)
1900/udp (v6)              ALLOW IN    Anywhere (v6)
8080:8082/tcp (v6)         ALLOW IN    Anywhere (v6)
20/tcp (v6)                ALLOW IN    Anywhere (v6)
21/tcp (v6)                ALLOW IN    Anywhere (v6)
40000:40050/tcp (v6)       ALLOW IN    Anywhere (v6)


```


I have 20,21,22,40000-40050 ports all forwarded to the NAT'd IP of the server.

There are not blocks in ufw log when trying to connect but I DO see messages in vsftpd.log that indicate a connection is made so I assume port forwarding and ufw is working as it should, leading me to believe the problem is with vsftpd itself. 

Open port checks (Canyouseeme.org) lend the following:

Port 20 - immediately rejected
Port 21 - Success!
Port 22 - Success!
40000 (any in the range) - Immediately rejected

When attempting to connect via Filezilla, I get the following logs:

Status:    Resolving address of oh.domain.org
Status:    Connecting to 76.15.1.1xx:21...
Error:    Connection timed out after 20 seconds of inactivity
Error:    Could not connect to server
Status:    Waiting to retry...
Status:    Resolving address of oh.domain.org
Status:    Connecting to 76.15.1.1xx:21...
Error:    Connection timed out after 20 seconds of inactivity
Error:    Could not connect to server


Finally, with this connection, this is what I get in the vsftpd.log:
```
Sun Nov 27 17:02:22 2016 [pid 20423] CONNECT: Client "52.202.1.xxx" <-this is where it should be coming from

```
There is nothing else in the log after this. From this it would appear it should be working, but it is not

---

### Post by TheFu on 2016-11-27
Simple solution is to use sftp and openssh-server (which includes it).  openssh-server is how almost every Linux server is remotely managed.  1 port/tcp covers remote shell, sftp, scp, remote desktop (via NX), VPN, proxy, remote editing .... that that's just off the top of my head.

If you don't have a specific requirement to use the ftps, purge that.  I really wish they'd stop teaching that as a viable solution.

filezilla and winscp support sftp, BTW.  Every other networked OS that I know has built-in or great sftp clients too.  For example, pretty much every GUI file manager on Linux has it built-in.  Just use sftp:// in the URL.

---

### Post by shelzmike2 on 2016-11-27
I get what you are saying and I could have done that, but this is for a very specific, very short in duration, purpose. 

Update on the situation:

It apparently has been working the whole time. I wasn't thinking when testing and that is what made it seem it wasn't working. The problem? I was attempting to connect to external FTP via URL from the same lan the FTP server was on! I got someone completely outside of my network to try and it worked perfectly. Duh...so much time wasted on such a simple problem!

---

### Post by darkod on 2016-11-28
Please mark it as solved so that people know it is. You can do that in Thread Tools above the first post.

---

