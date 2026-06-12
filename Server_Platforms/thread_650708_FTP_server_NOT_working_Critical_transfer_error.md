---
title: "FTP server NOT working: Critical transfer error"
date: 2007-12-26
forum: Server Platforms
---

### Post by cocotu on 2007-12-26
I already installed vsftpd and played with the vsftpd.conf file.  I'm using Filezilla to upload files and I'm unable to.  I get:

Critical Transfer Error

some people suggest is a firewall issue.  But how do I find out this?  In order to install the FTP server I followed the instructions from here:

[https://help.ubuntu.com/7.10/server/C/ftp-server.html](https://help.ubuntu.com/7.10/server/C/ftp-server.html)

thanks..

---

### Post by bunnynuts on 2007-12-26
First, lets look at your permissions. What are the permissions for the directory that you are uploading to, and who is the owner of the directory? It could be that your ftp user doesn't have sufficient permission. 

Second, are you running iptables or have you configured any firewall software? Also, is your server behind a router? If so you need to allow whatever port you are using for ftp (default of course being 21). 

Finally, it may help if you post your vsftpd.conf file (feel free to replace the semi-sensitive information). 

Hope this helps, will check back later to see if I can offer an other help.

---

### Post by cocotu on 2007-12-27
Strange enough when I came back this morning to work, I'm not able to connect at all:

1.  The permissions are: drwxr-xr-x and I am the owner of the directory(my home dir).  I tried to upload to different dirs and also tired changing permissions to other dirs to 777 and still can't upload.
2.  I'm NOT running IPtables or I have NOT configured any firewall software.  I'm NOT behind a router.  I'm inside our LAN and I was able to connect to the server using Filezilla, but not able to upload anything.  I also tried a different FTP client and same results.
3. here is the vsftpd.conf:

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
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
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
chown_uploads=YES
chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format
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
#chroot_local_user=YES
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
#
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
secure_chroot_dir=/var/run/vsftpd
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

Thanks bunnynuts!

---

### Post by ruibernardo on 2007-12-27
> **cocotu said:**
> # Allow anonymous FTP? (Beware - allowed by default if you comment this out).
** anonymous_enable=NO**
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
...
# If you want, you can arrange** for uploaded anonymous** files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=**whoever**

Hi cocofu, 

since you're not using anonymous logins, there is no use to set the "chown_uploads" and "chown_username" options. I would suggest you to comment them back and restart vsftpd:
```
sudo /etc/init.d/vsftpd restart
```If you do want  to use those two options, the username must be an existing one. Check if the user "whoever" really exists.

Good luck.

---

### Post by cocotu on 2007-12-27
that did the trick my friend, thanks!  I want to be able to upload to the /var/www and its giving me "critical transfer error" I think I need to change the permissions, currently they are:

drwxrwxr-x 14 root root  4096 2007-11-05 12:45 var
drwxrwxr-x  5 root root  4096 2007-12-26 15:29 www

do I need to make then 777?
thanks

---

### Post by bunnynuts on 2007-12-27
Good to see that this is working for your now. If you are going to allow anonymous upload then you will need to have the 777 permissions. However, this may not be the wisest choice for the /var/www folder. You may want to make a new directory in the /home directory and use this one. Otherwise you may want to create a new ftp only user with limited permissions (no shell) and have this user be allowed to upload to the /var/www folder.

---

