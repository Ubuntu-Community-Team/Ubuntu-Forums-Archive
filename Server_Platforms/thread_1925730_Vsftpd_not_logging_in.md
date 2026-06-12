---
title: "Vsftpd not logging in"
date: 2012-02-15
forum: Server Platforms
---

### Post by Clarkey252 on 2012-02-15
Sorry if this is a duplicate post, I have seen similar but haven't been able to solve my problem as of yet.

Im getting the errors:
Response:	530 Login incorrect.
Error:	Critical error
Error:	Could not connect to server

There is one user on my server and the username is in the user list file, I'm starting to think that this may be my problem, is it possible to log in with your only superuser? (also I'm trying to log on with the same credentials, not sure if I should set another password somewhere)

Here is my vsftpd.conf file:
```

#Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# If you do not change anything here you will have a minimum setup for an
# anonymus FTP server.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.

# General Settings
#
# Uncomment this to enable any form of FTP write command.
#
write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
#
dirmessage_enable=YES
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#
#nopriv_user=ftpsecure
#
# You may fully customise the login banner string:
#
ftpd_banner="Welcome to GIGABOX FTP service."
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#
#ls_recurse_enable=YES
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#
#deny_email_enable=YES
#
# (default follows)
#
#banned_email_file=/etc/vsftpd.banned_emails
#
# If enabled, all user and group information in
# directory listings will be displayed as "ftp".
#
#hide_ids=YES

# Local FTP user Settings
#
# Uncomment this to allow local users to log in.
#
local_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#
local_umask=022
#
# Uncomment to put local users in a chroot() jail in their home directory
# after login.
#
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#
#chroot_list_enable=YES
#
# (default follows)
#
#chroot_list_file=/etc/vsftpd.chroot_list
#
# The maximum data transfer rate permitted, in bytes per second, for
# local authenticated users. The default is 0 (unlimited).
#
#local_max_rate=7200

# Anonymus FTP user Settings
#
# Allow anonymous FTP?
#
anonymous_enable=NO
#
# Anonymous users will only be allowed to download files which are
# world readable.
#
#anon_world_readable_only=YES
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#
anon_upload_enable=NO
#
# Default umask for anonymus users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#
anon_umask=022
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#
#anon_mkdir_write_enable=YES
#
# Uncomment this to enable anonymus FTP users to perform other write operations
# like deletion and renaming.
#
#anon_other_write_enable=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#
#chown_uploads=YES
#chown_username=root
#
# The maximum data transfer rate permitted, in bytes per second, for anonymous
# authenticated users. The default is 0 (unlimited).
#
#anon_max_rate=7200

# Log Settings
#
# Log to the syslog daemon instead of using an logfile.
#
syslog_enable=YES
#
# Uncomment this to log all FTP requests and responses.
#
log_ftp_protocol=YES
#
# Activate logging of uploads/downloads.
#
#xferlog_enable=YES
#
# You may override where the log file goes if you like. The default is shown
# below.
#
vsftpd_log_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note: This disables the normal logging unless you enable dual_log_enable below.
#
#xferlog_std_format=YES
#
# You may override where the log file goes if you like. The default is shown
# below.
#
#xferlog_file=/var/log/xferlog
#
# Enable this to have booth logfiles. Standard xferlog and vsftpd's own style log.
#
#dual_log_enable=YES
#
# Uncomment this to enable session status information in the system process listing.
#
#setproctitle_enable=YES

# Transfer Settings
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
#
connect_from_port_20=YES
#
# You may change the default value for timing out an idle session.
#
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#
#data_connection_timeout=120
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that turning on ascii_download_enable enables malicious remote parties
# to consume your I/O resources, by issuing the command "SIZE /big/file" in
# ASCII mode.
# These ASCII options are split into upload and download because you may wish
# to enable ASCII uploads (to prevent uploaded scripts etc. from breaking),
# without the DoS risk of SIZE and ASCII downloads. ASCII mangling should be
# on the client anyway..
#
ascii_upload_enable=YES
ascii_download_enable=YES
#
# Set to NO if you want to disallow the PASV method of obtaining a data
# connection.
#
#pasv_enable=NO

# PAM setting. Do NOT change this unless you know what you do!
#
pam_service_name=vsftpd

# Set listen=YES if you want vsftpd to run standalone
#
listen=YES

```

---

### Post by Lars Noodén on 2012-02-15
Are you sure you even want to mess with [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)?  If you are looking to transfer files securely, then SFTP will do the job and it comes as part of SSH which you likely have already installed.  Regular SFTP clients include programs like FileZilla and Nautilus, so no special software is needed on the client side.

---

### Post by Clarkey252 on 2012-02-15
WOW! Openssh server is soooo much easier, I was going wrong because I changed the listening port for the ssh service and if you dont put the stfp:// in FileZilla it doesn't pick it up as an Sftp server even if you sepcify the port.

---

