---
title: "problem giving new users ftp access"
date: 2011-03-03
forum: Server Platforms
---

### Post by nucleuskore on 2011-03-03
I have successfully setup Ubuntu Server, to act as a SAMBA file server with multiple users. 

I have now installed vsftpd with the intention of giving the users access to their home directories (which they already have access to via SAMBA). 
However only the user who was created first on the system, myself, is able to login to the ftp server over the local network. All other user accounts give the 530 login incorrect message.

I am not able to understand why these users are being denied ftp access. Am enclosing my vsftpd file below. Thanks in advance !

----------------------------------------------------------------------------

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




#IFACE=eth0
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

#anonymous_enable=YES 
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
#chroot_local_user=YES

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
#rsa_cert_file=/etc/ssl/private/vsftpd.pem

---

### Post by bsntech on 2011-03-03
Are your users real user accounts on the system - or are the virtual user accounts?

I use virtual user accounts - which are held in a MySQL database.  I then use ProFTP with the MySQL plugin which pulls the usernames from the database.

So, not sure what you are using - but if you are using virtual accounts, this would be why they are unable to login.

Brian S.
[http://www.bsntech.com]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/")

---

### Post by nucleuskore on 2011-03-03
All my users are system users. The do not have sudo rights

---

### Post by Lars Noodén on 2011-03-04
> **nucleuskore said:**
> All my users are system users. The do not have sudo rights

I would then recommend giving SFTP a try, because if you have SSH access then  you already have SFTP access.  Your users probably have at least one [GUI SFTP client](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients) in use on a daily basis.  

Going with SFTP reduces the number and complexity of server configurations needed.  Plus your users can use regular clients and won't need special software.

---

### Post by nucleuskore on 2011-03-16
**I solved the problem.** 

The problem:

I was able to login through ftp as the first system user I created at install.

I was not able to login through ftp as the two new system users I created after I installed SAMBA but BEFORE I installed vsftpd

I was able to login through ftp as all the other system users I created AFTER I installed vsftpd

Solution: 

I simply created two new users, copied all the files to those accounts in command line, and deleted the two old user accounts.

I would appreciate if someone could think of a more logical solution.

---

