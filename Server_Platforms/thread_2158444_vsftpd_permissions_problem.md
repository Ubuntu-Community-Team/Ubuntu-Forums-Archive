---
title: "vsftpd permissions problem"
date: 2013-06-29
forum: Server Platforms
---

### Post by kaptenen on 2013-06-29
Hello,

i have just started up a new webserver on my ubuntu 12.10 server and i got a problem with my vsftpd. So the problem is that i can't get the files/folders i upload with the correct permissions at all. I have done some reading on umask
and so some hours now and i still can't fix it. I need my folders and files to be writable(777 or 755 don't remember). And at the same time i have a problem that the ftp user can not delete some of the folders he/she uploads.

[B]My vsftpd config:
```
[/B]# Example config file /etc/vsftpd.conf#
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
local_umask=002
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
ftpd_banner=Welcome Erci-Verkstad.se FTP Service
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
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
[B]
```
[/B]
Thanks for any help!

---

### Post by Kujua on 2013-06-29
Can you be more specific on what permissions you want exactly? And what permissions are the uploaded files having right now?

By default mode for uploaded files will be 666 minus local_umask. So if your umask is 002, files should get 664, which **IS** writable by owner and group. It does not have to be 777 or 755 for files. For directories mode will be 777 minus local_umask.

If you are observing a different behaviour, then perhaps your base mode for files is different. In that case you can set the base mode with 'file_open_mode' option. Check 'man vsftpd.conf' for details. Also, have a look at this: [http://ubuntuforums.org/showthread.php?t=1963231](http://ubuntuforums.org/showthread.php?t=1963231)

Regarding not being able to delete some folders: This might be because the folders are not empty.

---

### Post by Alan_Halls on 2014-02-26
After searching all over, I finally found the solution for myself over on serverfault. Posting it here as well to increase odds of someone finding the information.
You need to set your umask, it can be set in the vsftpd config file (/etc/vsftpd.conf) 

  For the mask to work properly (even without anonymous access)** it seems necessary to set anon_upload_enable=YES** and anon_mkdir_write_enable=YES.  If these are not set, writing, reading and executing will not be  allowed for groups or others on files uploaded via ftp (even though the  standard privileges may be set for something else).

  In your case, if you need user-authenticated access, you should set the following:
  anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=0002
anon_upload_enable=YES
anon_mkdir_write_enable=YES
file_open_mode=0777
  Here, file_open_mode sets the default setting of files. 777 makes it readable, writable and executable for anyone. With local_umask set to 002, this gives you 775, or you could do 022 for 755

  Notice that local_umask defaults to 077, disabling groups and others to access files in any way (hence it is set here).

  Further reading: [https://security.appspot.com/vsftpd/vsftpd_conf.html](https://security.appspot.com/vsftpd/vsftpd_conf.html)

---

### Post by fernmark on 2014-10-27
> **Alan_Halls said:**
> After searching all over, I finally found the solution for myself over on serverfault. Posting it here as well to increase odds of someone finding the information....

Thank you.  This saved me additional time and headache searching for the answer.

---

