---
title: "VSFTPd + iptables Delay"
date: 2012-02-07
forum: Server Platforms
---

### Post by Skye Menjou on 2012-02-07
So I have an Ubuntu 10.10 server VPS(Openvz).
The issue is with VSFTPD i get a delay when I enter Passive mode with an FTP client, about 5-10 seconds when I upload,list directory or anything else. Tested with multiple clients.
This only happens with iptables rules configured.
I set up a specific range in VSFTPD for the passive ports and opened them in iptables.
The openvz node has ip_conntrack_ftp enabled.

```

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
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
#xferlog_enable=YES
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
idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
data_connection_timeout=120
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
ftpd_banner=Welcome to SkyeDax
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
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_local_user=YES
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
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
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

rsa_cert_file=/etc/vsftpd/vsftpd.pem
ssl_enable=NO
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
#ftp_username=
#max_per_ip=
pasv_min_port=10050
pasv_max_port=10060
pasv_address=[REDACTED PUBLIC IP]
log_ftp_protocol=YES

```

and the iptables shell script:

```
iptables -F
iptables -P INPUT DROP
iptables -A INPUT -p tcp  --dport 10050:10060  -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -p 47 -j ACCEPT
iptables -A INPUT -i ppp0 -j ACCEPT

iptables -A INPUT -i venet0 -p tcp --dport [REDACTED] -m state --state NEW -m recent --set --name SSH
iptables -A INPUT -i venet0 -p tcp --dport [REDACTED] -m state --state NEW -m recent --update --seconds 60 --hitcount 8 --rttl --name SSH -j DROP


iptables -A INPUT -i venet0 -p tcp -m multiport --dports 53,500,108,1723,20:21,6669,80,443,25,143,993 -m state --state NEW,ESTABLISHED -j ACCEPT

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -i lo -j ACCEPT
iptables -A INPUT -p udp -i venet0  -m multiport --dports 53,10050:10060 -j ACCEPT


# PPTP IP forwarding

iptables -A POSTROUTING -t nat -o venet0 -j MASQUERADE
iptables -A POSTROUTING -t nat -o ppp0 -j MASQUERADE
iptables -t nat -A POSTROUTING  -j SNAT --to-source 108.174.51.210
iptables -t nat -A POSTROUTING -s 192.168.3.0/24 -j SNAT --to-source [REDACTED PUBLIC IP]

```

I have to admit that iptables file isn't pretty, I am a beginner to iptables when it comes to it, feel free to give constructive critism.
Like I said before, I think the issue lies with iptables since without it configured it works fine.

---

