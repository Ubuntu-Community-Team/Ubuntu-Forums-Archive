---
title: "vsftpd server setup"
date: 2013-01-14
forum: Server Platforms
---

### Post by ZenMasta on 2013-01-14
I just provisioned a new vps and trying to setup ftp server

I'm trying to follow this guide which seams very simple to do. But I must be missing something because I am getting errors when I try to login.

[https://help.ubuntu.com/10.04/serverguide/ftp-server.html](https://help.ubuntu.com/10.04/serverguide/ftp-server.html)

filezilla says:
500 OOPS: could not read chroot() list file:/etc/vsftpd.chroot_list

Heres my vsftpd.conf I've bolded everything I changed according to the guide.

I'm curious also about the bold italic entry that is commented out as it is the same as uncommented below... I tried one or the other incase that made any difference. Thanks!

of course I also sudo /etc/init.d/vsftpd restart

> # Example config file /etc/vsftpd.conf
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
**local_enable=YES**
#
# Uncomment this to enable any form of FTP write command.
**write_enable=YES**
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
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
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
***#chroot_local_user=YES***
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
[B]chroot_local_user=YES
chroot_list_enable=YES[/B]
# (default follows)
**chroot_list_file=/etc/vsftpd.chroot_list**
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
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key




---

### Post by apohal9 on 2013-01-14
Is the file **/etc/vsftpd.chroot_list** readable by the user vsftpd is running as?
> ls -la /etc/vsftpd.*

---

### Post by ZenMasta on 2013-01-14
I have another server running 10.10 and its also owned by root but users can ftp just fine. Doesn't seem logical to me that a regular user would have access to that file.

ls -la /etc/vsftpd.*
-rw-r--r-- 1 root root 5650 Jan 14 11:08 /etc/vsftpd.conf

There is no actual file /etc/vsftpd.chroot_list  on the old server (which has been running/working as expected for almost 2 years), or the new server

So I don't know where this actually comes from, aside from it being documented in the conf

---

### Post by LHammonds on 2013-01-14
I also tried the official dox and other various sites and found most covering only the minimal basic setup.  I figured out how to set it up using FTP over SSL (FTPS) and documented how I accomplished it in my sig.

LHammonds

---

### Post by ZenMasta on 2013-01-14
I just wish I knew what was wrong with the current config. I had just done this last week also on 12.10 and it was working fine. Not sure what the deal is.

---

### Post by ZenMasta on 2013-01-14
I compared the conf with my old server that is working

I commented out 

chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list

seems to be working fine now

---

### Post by apohal9 on 2013-01-15
So the same config works on your 10.10 and 12.04 but not on 10.04?

Hmm, strange. My guess would be, that these servers use different vsftpd versions that behave different when they cannot find the chroot list file when you enabled this feature by setting

chroot_list_enable=YES

Anyways, the error is quite clear:
500 OOPS: could not read chroot() list file:/etc/vsftpd.chroot_list

---

### Post by ZenMasta on 2013-01-15
I'm sure they are different vsftpd versions but the config is basically the same. Originally I was trying to follow the guide that I had linked to in the first post. But when I compared configs with the old server, which works. I thought I would try to copy it and so its fine now.

I'm happy so long as it works.

---

### Post by mörgæs on 2013-01-15
It's best to mark the thread 'solved' using 'thread tools'.

Have done it this time.

---

