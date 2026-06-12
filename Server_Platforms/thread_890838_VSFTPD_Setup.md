---
title: "VSFTPD Setup"
date: 2008-08-15
forum: Server Platforms
---

### Post by austinderrick2 on 2008-08-15
Ok, I've followed several different versions of how to install this, however, I am still having trouble.

Everytime I try to login I get an "Incorrect Login" message.

I can ssh into the box with the same credentials, so I know they are correct... Any ideas?

> 
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
#connect_from_port_20=YES
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
#rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
#rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


---

### Post by dca on 2008-08-15
Try uncommenting this line:
 
chroot_local_user=YES
 
..then restart FTP service (sudo /etc/init.d/vsftpd) or restart server and try that...

---

### Post by dca on 2008-08-15
The best I can see, your vsftpd.conf would now look identical to mine.  My server name and (only) user name on system is the same so when prompted to login I just use that same username & p/w.

---

### Post by dca on 2008-08-15
After restarting service and making change see if you can access by typing at CLI:
 
ftp localhost
 
...if you succeed there than I would go to remote system on same network segment and see if it still prompts for login through web browser or gFTP...

---

### Post by austinderrick2 on 2008-08-15
I have uncommented the specified line and restarted the service.

I still cannot access the FTP (Even from localhost as suggested.)

I tryed with my regular username and password as well as one I made specifically for FTP.

:confused:

---

### Post by hux on 2008-08-28
The chroot_local_user setting should not affect whether or not you can log in, so I'd comment it back out at this point for the sake of troubleshooting.

What do you have in /var/log/vsftpd.log?

Did you check the instructions in the "INSTALL" file? There are a few things you need to do regarding users, setting folder permissions, etc., before it will work.

---

### Post by Tux+ on 2008-08-29
Try uncommenting the line:

> chroot_list_user=YES

as well the following line:


> chroot_list_file=/etc/vsftpd.chroot_list

Leave the list file empty / as it is.

Restart vsftpd when your done.

---

### Post by sahwan on 2008-08-29
same times if you install ssh & ftp it wont be okay

if this is jest change the ssh port

---

### Post by Alpha01 on 2008-08-29
> **austinderrick2 said:**
> Ok, I've followed several different versions of how to install this, however, I am still having trouble.

Everytime I try to login I get an "Incorrect Login" message.

I can ssh into the box with the same credentials, so I know they are correct... Any ideas?

I'd suggest changing the default login shell to /bin/false/. Make sure you add the /bin/false entry to the /etc/shells file. I had the exact same problem and the solutions was changing the login shell to /bin/false/ (with a a forward slash at the end). This is done to give the user FTP access only. If you still want shell access try adding the forward slash at the end of the default log in shell (/bin/bash/)

Hope this helps

---

### Post by johngreth on 2010-02-10
> **Alpha01 said:**
> I'd suggest changing the default login shell to /bin/false/. Make sure you add the /bin/false entry to the /etc/shells file. I had the exact same problem and the solutions was changing the login shell to /bin/false/ (with a a forward slash at the end). This is done to give the user FTP access only. If you still want shell access try adding the forward slash at the end of the default log in shell (/bin/bash/)

Could you put that in English? I have no idea what the default login shell is or how to set it. Thanks.

---

