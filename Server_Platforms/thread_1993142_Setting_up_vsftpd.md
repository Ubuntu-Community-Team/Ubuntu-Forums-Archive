---
title: "Setting up vsftpd"
date: 2012-06-01
forum: Server Platforms
---

### Post by lorenzone92 on 2012-06-01
Uhm.. I need a little help with users permissions I think.

Here's the content of the /etc/vsftpd.conf file:
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
ftpd_banner=Welcome to our FTP service.
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
rsa_cert_file=/etc/ssl/private/vsftpd.pem

listen_port=21
```

And I have a vsftpd.chroot_list file with a list (well.. just one) of users with the perms to use ftp (as far as I understood). Just the name of the users.

To create the user whom name is in the vsftpd.chroot_list file I used the command:
useradd -d /home/www USERNAME

Then:
chown USERNAME /home/www/

and finally:
passwd USERNAME

When I try to connect via FTP using the credentials of this username I manage to connect!
The problems are:
1) I can access not only the dir /home/www/ but also parent dirs!
2) User doesn't have write perms..


**EDIT:** Of course I restarted the vsftpd process.

---

### Post by maverickaddicted on 2012-06-05
> **lorenzone92 said:**
> Uhm.. I need a little help with users permissions I think.

To create the user whom name is in the vsftpd.chroot_list file I used the command:
useradd -d /home/www USERNAME

Then:
chown USERNAME /home/www/

and finally:
passwd USERNAME

When I try to connect via FTP using the credentials of this username I manage to connect!
The problems are:
1) I can access not only the dir /home/www/ but also parent dirs!
2) User doesn't have write perms..

**EDIT:** Of course I restarted the vsftpd process.

Here is my vsftpd configuration file, check the bold line -

```

serveradmin@openserver:~$ cat /etc/vsftpd.conf
# /etc/vsftpd.conf - vsftpd configuration file
#
# Run standalone
listen=YES
#
# Allow anonymous FTP
anonymous_enable=NO
#
# Allow local users to log in
local_enable=YES
#
# Allow any form of FTP write command
write_enable=YES
#
# Default umask is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd)
[B]local_umask=002
anon_umask=002[/B]
#
# Allow the anonymous FTP user to upload files
anon_upload_enable=NO
#
# Allow the anonymous FTP user to be able to create new directories
anon_mkdir_write_enable=NO
#
# Activate directory messages
dirmessage_enable=YES
#
# Display directory listings with the time in your local time zone
use_localtime=YES
#
# Activate logging of uploads/downloads
[B]xferlog_enable=YES
chmod_enable=YES
dirlist_enable=YES
lock_upload_files=NO
virtual_use_local_privs=YES
chown_upload_mode=0777  # it is local development server only, that's why I have
file_open_mode=0777     # set it to 777, you can change accordingly [/B]
# Make sure PORT transfer connections originate from port 20 (ftp-data)
connect_from_port_20=YES
#
# Uploaded anonymous files to be owned by a different user
#chown_uploads=YES
#chown_username=whoever
#
# Log file path
#xferlog_file=/var/log/vsftpd.log
#
# Log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# Customise the login banner string
ftpd_banner=Welcome to OpenServer
#
# Use the contents of this file for the login banner
#banner_file=/etc/vsftpd/banner
#
# Restrict local users to their home directories
**chroot_local_user=YES**
#
# List of local users to chroot() to their home directory. If
# chroot_local_user is YES, then this list becomes a list of users to NOT
# chroot()
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd/chroot_list
#
# Activate the "-R" option to the builtin ls. This is disabled by default to
# avoid remote users being able to cause excessive I/O on large sites.
# However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option
ls_recurse_enable=YES
#
# Show textual names in the user and group fields of directory listings
text_userdb_names=YES
#
# Empty directory not writable by the ftp user as a secure chroot() jail at
# times vsftpd does not require filesystem access
secure_chroot_dir=/var/run/vsftpd/empty
#
# PAM service vsftpd will use
pam_service_name=vsftpd
serveradmin@openserver:~$

```

If you are facing permission problems, try to add your user to apache www-data group i.e. make www-data as primary group. And run this command -

```
sudo chown -Rf user:www-data /home/www/
```

This was the only solution that helped me with permission problem.

---

### Post by Lars Noodén on 2012-06-05
> **maverickaddicted said:**
> 

If you are facing permission problems, try to add your user to apache www-data group i.e. make www-data as primary group. And run this command -

```
sudo chown -Rf user:www-data /home/www/
```

This was the only solution that helped me with permission problem.

Please don't give write access to www-data.  That makes your system insecure.  If you are going to be sharing the folder among several users, then you will want to use groups, but at least make a fresh one.  The user and group www-data are reserved for [privilege separation](http://wiki.apache.org/httpd/PrivilegeSeparation) in the web server.  Trying to use it in other ways defeats the security advantage. 

Here's how you can make a new group and use in conjunction with Apache2's default virtual host:
```

# do once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add lorenzone92 webmasters

```

While we're at it, you might also want to reconsider the use of FTP and use SFTP instead.  

[list]
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

SFTP is built into clients like FileZilla, Thunar and Nautilus.

---

### Post by maverickaddicted on 2012-06-06
> **Lars Noodén said:**
> Please don't give write access to www-data.  That makes your system insecure.  If you are going to be sharing the folder among several users, then you will want to use groups, but at least make a fresh one.  The user and group www-data are reserved for [privilege separation](http://wiki.apache.org/httpd/PrivilegeSeparation) in the web server.  Trying to use it in other ways defeats the security advantage. 

Here's how you can make a new group and use in conjunction with Apache2's default virtual host:
```

# do once
sudo addgroup webmasters
sudo chgrp -R webmasters /var/www

sudo find /var/www -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add lorenzone92 webmasters

```

While we're at it, you might also want to reconsider the use of FTP and use SFTP instead.  

[list]
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[/list]

SFTP is built into clients like FileZilla, Thunar and Nautilus.

I have already tried that, but it doesn't work,whenever I upload some plugin or component from cms backend, it doesn't allow me to edit the uploaded files via ftp. It gives permission denied. However, when I change the permission as I have already shown you. Everything works perfectly. No permission problem.

---

### Post by Lars Noodén on 2012-06-06
> **maverickaddicted said:**
> I have already tried that, but it doesn't work,whenever I upload some plugin or component from cms backend, it doesn't allow me to edit the uploaded files via ftp. It gives permission denied. However, when I change the permission as I have already shown you. Everything works perfectly. No permission problem.

Strange. What are the default permissions of the files you upload using FTP?

ls -lh

---

### Post by Fatjoint on 2012-06-06
```

# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
chroot_list_enable=**NO**
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
```

Change chroot_list_enable to NO.

Your list of users becomes a list of users to chroot to their home directory.  Enabling chroot_list_enable allows them to traverse directories.

The other issue is the write permissions, and I would follow others advice regarding this.

---

### Post by maverickaddicted on 2012-06-06
> **Lars Noodén said:**
> Strange. What are the default permissions of the files you upload using FTP?

ls -lh

this is the part of the output -

```
-rw-r--r--  1 www-data www-data 1.6K 2010-12-29 09:35 robots.txt

```

---

