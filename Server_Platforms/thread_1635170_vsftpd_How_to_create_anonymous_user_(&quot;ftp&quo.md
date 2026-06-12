---
title: "vsftpd: How to create anonymous user (&quot;ftp&quot;) with password?"
date: 2010-12-01
forum: Server Platforms
---

### Post by dbsoundman on 2010-12-01
I configured a server with vsftpd, and what I want to do is force local users to use SSL (which I have done), and allow anonymous users on the "ftp" username to access the server with only a password and no SSL. Here is my configuration file:

```
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
anonymous_enable=YES
ftp_username=ftp
anon_root=/home/signaltraffic
anon_umask=0333
anon_upload_enable=NO
anon_world_readable_only=YES
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
no_anon_password=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
userlist_file=/etc/vsftpd_users
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
xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
xferlog_std_format=YES
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
#chroot_local_user=YES
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
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
#rsa_cert_file=/etc/ssl/private/vsftpd.pem

# These lines added via instructions on wiki.vpslink.com/Configuring_vsftpd_for_secure_connections_(TLS/SSL/SFTP):
ssl_enable=YES
allow_anon_ssl=NO
# the next two params actually force SSL
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
rsa_cert_file=/etc/vsftpd/vsftpd.pem

# These lines added via instructions on calomel.org/vsftpd.html for logging.
# To see connections, execute ' watch ps -C vsftpd -o user,pid,stime,cmd '.
setproctitle_enable=YES

```

My /etc/vsftpd_users file contains all the local users I want to give access, as well as the "ftp" user, which I added as a local user, assigned a password, and made sure was part of the group "ftp". This actually works fine; the **problem** is that if I simply go to [ftp://my.domain.com](ftp://my.domain.com), I'm presented with the anonymous ftp directory WITHOUT having to enter a password; in order to be prompted, I have to enter [ftp://ftp@my.domain.com](ftp://ftp@my.domain.com).

So, what I want to do is to "hide" the anonymous ftp page until a password is entered. I'm thinking that I need to be able to disable the "anonymous" user in order to do this, but I can't seem to figure out how to do that. I tried using "ftp_username=ftp", but that didn't work. I even tried adding "anonymous" as a local user, giving it the same password as "ftp", and adding it to the vsftpd_users file, to no avail. The only thing I did NOT do when I added the user "anonymous" is create a home directory for this user; I figured since the "ftp" user didn't have one, "anonymous" didn't need one, as I redirected the base directory for anonymous logins anyway.

What am I doing wrong here? I'd appreciate suggestions!

Thanks,
-Dan

---

### Post by LiLoather on 2011-03-18
Pity no-one responded to this as I would have thought it a pretty basic function - giving local users access to their home directories is OK but if I want to transfer a file to or from a friend, or make one available to a group if not everyone I don't want to have to give out my password.  So a 'public venue' accessible by ftp would seem to be useful at any time.

---

### Post by Foeburner on 2011-03-23
i am also looking to add this to my existing ftp server where each user logs into their home folder and placing files in the public folder will allow access to everyone, like a meeting room. If a user logs in anonymously, they go strait to that public folder. 

Can this even be done?

---

### Post by LostInSpace82 on 2012-02-04
This is an old thread, so my post will most likely not be useful to the OP, however I came upon it by searching for the same thing, before figuring out the obvious solution. So, hopefully this will be useful to someone else in the future.

Why go through the trouble of allowing anonymous login only to force authentication? Simply create a directory dedicated to "anonymous" (group) activity and a user to be chrooted to that dir. That's it! #-o

---

