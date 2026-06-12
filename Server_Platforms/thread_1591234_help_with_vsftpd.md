---
title: "help with vsftpd"
date: 2010-10-09
forum: Server Platforms
---

### Post by antonvrg on 2010-10-09
ok so i want to set up an FTP server off my ubuntu box over my home network. I have installed vsftpd and have tried adding a user for a while. i have a user called ftp (it will be the only user). when i logon to this user in Filezilla i cant add files to the server. i want to make it so it can. i would also like SSH but if i cant get it then i wont worry (not to sure i need it). 

what i have:

vsftp.conf & vsftpd.chroot_list

vsftpd.chroot_list has the following:

```
ftp
666
```

and vsftp.conf has:

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
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
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
#ftpd_banner=Welcome to Anton's FTP service.
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
ssl_enable=Yes
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
```

what am i doing wrong?

any questions just ask. any help would be greatly apriciated.

Thanks in advance.
Anton

---

### Post by Jose Catre-Vandis on 2010-10-09
Uncomment here:
```
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
```

---

### Post by antonvrg on 2010-10-09
> **Jose Catre-Vandis said:**
> Uncomment here:
```
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
```

what do i change it to?

---

### Post by luvshines on 2010-10-09
> **antonvrg said:**
> what do i change it to?

It says uncomment, so remove the # in the beginning. It should look like:
```
# Uncomment this to enable any form of FTP write command.
write_enable=YES
```

You may require to sudo to achieve that.
Then restart the service

---

### Post by antonvrg on 2010-10-09
ok i changed it i tried to restart and got this

```
made2shred@made2shred-desktop:~$ sudo /etc/init.d/vsftpd restart
[sudo] password for made2shred: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart vsftpd
vsftpd start/running, process 5538
made2shred@made2shred-desktop:~$ 

```

now it wont connect to the server using filezilla (it says)

```
Status:	Resolving address of made2shred-desktop
Status:	Connecting to 127.0.1.1:21...
Status:	Connection attempt failed with "ECONNREFUSED - Connection refused by server".
Error:	Could not connect to server
```

---

### Post by Jose Catre-Vandis on 2010-10-09
Are you sure it's running? Try
```
sudo service vsftpd restart
```

You should get:
```

* Stopping FTP server: vsftpd   [OK] 
* Starting FTP server: vsftpd   [OK]
```

---

### Post by antonvrg on 2010-10-09
> **Jose Catre-Vandis said:**
> Are you sure it's running? Try
```
sudo service vsftpd restart
```

You should get:
```

* Stopping FTP server: vsftpd   [OK] 
* Starting FTP server: vsftpd   [OK]
```

i get this:

```
restart: Unknown instance: 

```

---

### Post by Jose Catre-Vandis on 2010-10-10
Try
```
sudo service vsftpd start
```

---

### Post by antonvrg on 2010-10-10
> **Jose Catre-Vandis said:**
> Try
```
sudo service vsftpd start
```

ok that worked but now ive got an error in filezilla

```
Status:	Resolving address of made2shred-desktop
Status:	Connecting to 127.0.1.1:21...
Status:	Connection established, waiting for welcome message...
Response:	500 OOPS: cannot locate user entry:apache
Error:	Critical error
Error:	Could not connect to server
```

---

### Post by windsxs on 2010-10-10
Hi, 
yesterday i had same problem with Dreamveawer. I figured out, that you need to do this:
```
chown <dir> <user>
chmod 777 <dir>
```

in /etc/vsftpd.conf make theese "local_enable=YES" and "write_enable=YES" and then restart server.

And I think that user should be added to some group, which can access that files. (not figured how, but i'll try doing this myself at evening :rolleyes: )

---

