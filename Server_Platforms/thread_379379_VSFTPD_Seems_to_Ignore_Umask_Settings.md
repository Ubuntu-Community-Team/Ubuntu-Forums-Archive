---
title: "VSFTPD Seems to Ignore Umask Settings"
date: 2007-03-08
forum: Server Platforms
---

### Post by coxc24 on 2007-03-08
No matter what I do, vsftpd seems to ignore my umask settings. I have searched high and low but seem to hit the same problem. This is a Debian 3.1 (Sarge) install but the basis is of course the same! If I don't find an answer I might give Dapper a blast to see if it is the package, which I doubt.

My vsftpd.conf file is:

> # Run standalone?  vsftpd can run either from an inetd or as a standalone
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
local_umask=027
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
# Beware that turning on ascii_download_enable enables malicious remote parties
# to consume your I/O resources, by issuing the command "SIZE /big/file" in
# ASCII mode.
# These ASCII options are split into upload and download because you may wish
# to enable ASCII uploads (to prevent uploaded scripts etc. from breaking),
# without the DoS risk of SIZE and ASCII downloads. ASCII mangling should be
# on the client anyway..
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
rsa_cert_file=/etc/ssl/certs/vsftpd.pem

If I upload a file through gFTP or Konqueror (I use Kubutnu) it takes the permissions that already apply to the file and uses them on the server. So the file starts with the permissions:

> -rw-rw-rw- 1 chris chris 0 2007-03-08 17:26 Test

and then has the same permissions on the server:

> -rw-rw-rw-  1 chris ftp 0 2007-03-08 17:27 Test

The only thing that gets changed is the group, which is as I want it. Can anyone tell me what I am missing?

---

### Post by Mr. C. on 2007-03-08
You need to tell vsftpd to re-read its configuration file:

/etc/init.d/vsftpd reload

MrC

---

### Post by coxc24 on 2007-03-09
I'm sure I had tried reload, but just tried it anyway and the permissions of the file are still the same. Any other ideas?

---

### Post by Mr. C. on 2007-03-09
Did you remove the destination file before attempting to push the file again?  Permissions are retained otherwise.

Beyond that, I'd need to see your results, not interpretation. The system works.

MrC

---

### Post by coxy on 2007-03-11
I removed the file and the permissions were still the same after another upload. What information would you need to advise me further? This one has really got me stumped!

I have changed my user names from cox24 to coxy

Thanks

---

### Post by Mr. C. on 2007-03-11
If this is true, then one or more are the likely culprits:

1) vsftpd was not restarted after changes to vsftpd.conf
2) the vsftpd.conf file you are changing is not the same one vsftpd is using
3) vsftpd is installed in two locations, or is being launched by two differnt methods (xinetd, /etc/init.d), which is causing #2 above.  See /etc/init.d/vsftpd in any case.
4) your client is changing permissions

The system works. I tested your exact configuration before I posted; it worked.

MrC

---

### Post by coxy on 2007-03-12
Ok then, I checked and it is only running from the one location.

How is it possible for the client to change the permissions? Should it not create it with what the server tells it to? I have used both Konquer and Gftp and found the same results.

---

### Post by Mr. C. on 2007-03-12
The FTP protocol has a chmod command.  

```
$ ftp
ftp> help chmod
chmod           change file permissions of remote file
```


Here's an example of a Windows client.  Permissions were 700, and I changed them to 777.

MrC

---

### Post by coxy on 2007-03-16
I see, and as the owner of the file the user can set any permissions it likes.

Thanks for your help, much appreciated!

---

### Post by Mr. C. on 2007-03-16
You can also change

```
file_open_mode
```

to suit your needs.  Thi sets the mode for newly created files/dirs.  Umask is used on top of that.

And also:

```
chmod_enable No
```

and

```
cmds_allowed=*[.... list of allowed FTP commands - exclude chmod ]*
```

There many controls explained in

```
man vfstpd.conf
```
MrC

---

