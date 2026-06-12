---
title: "vsFTPd config question"
date: 2009-10-30
forum: Server Platforms
---

### Post by dm1tr1y on 2009-10-30
Hello.

I'm trying to configure vsFTPd server but i have a very silly problem...

I've installed Ubuntu server 9.10 with LAMP pakage and then manually installed vsFTPd using this command:
```
sudo apt-get install vsftpd
```After that i've executed this commands to provide anonymous access to the Apache www root directory via FTP:
```
sudo usermod -d /var/www ftp 
sudo /etc/init.d/vsftpd restart
```I've accessed this FTP from another PC and I've seen WWW root directory in my FTP client.

Because i want to allow READ/WRITE anonymous access to WWW root directory, I executed the following:
```
sudo vi /etc/vsftpd.conf
```And uncommented:
```
anon_upload_enable=YES
write_enable=YES
```After this I've executed:
```
sudo /etc/init.d/vsftpd restart
```After all that I've done, I connected remotly via FTP to my UBUNTU FTP SERVER.
Now I can browse FTP root directory but can't write anything there...
FTP client shows me this:
```
An error occured coping a file to the FTP server. Make sure you have permission to put files on the server.
Details:
200 Switching to Binary mode.
227 Entering Passive Mode (192,168,103,19,177,94).
553 Could not create file.
```Please, help me, what is wrong?

---

### Post by dm1tr1y on 2009-10-30
Also, I've tryed to change WWW directory access rights:
```
sudo chmod 777 /var/www
```
But after I've done this, FTP server started to ask my username and password for access...
And my UBUNTU users login and password - were wrong.... And if I enterse Anonymous as username and left passowrd field blank, FTP server not allowed me to access again...

:(:(:(

---

### Post by Lars Noodén on 2009-10-30
Ok.  First, please don't use FTP to enter any regular system usernames or passwords.  Sooner or later your machine will get cracked as a result.  The situation is a bit better if you are at least using FTPS.

Second, allowing anonymous upload to your web server means that every minute, you will have to supervise the content.  

So can we step back a bit and, without naming any protocols or software, ask what your main goals are?

---

### Post by dm1tr1y on 2009-10-30
Thank you for your answer.

You are absolutly right, but security is not a problem. I'm configuring internal server for my test/personal tasks.

My goal is to configuge simple LAMP server with FTP support. I want to put my PHP files into Apache WWW root using FTP.

But i can't configure FTP :(

---

### Post by Grim76 on 2009-10-30
Post a copy of your configuration so that we can see if there is something out of place.

---

### Post by dm1tr1y on 2009-10-30
This is my /etc/vsftpd.conf file:

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
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
#local_enable=YES
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
anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
anon_mkdir_write_enable=YES
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
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem

```As I understand, everything is OK here.
I modifyed only this:
```
anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
```Rights on APACHE WWW ROOT directory are: drwxr-xr-x

So, when I connect to this FTP server, I can **read **everything right, bt I can't **write **and **create directoryes**...

---

### Post by Grim76 on 2009-10-30
Who is the owner of the directory?  Sounds like the ftp user doesn't have permissions to write to the location.

---

### Post by dm1tr1y on 2009-10-30
Owner of /var/www - is a ROOT user

---

### Post by Grim76 on 2009-10-30
More than likely the error is related to ftp not having permissions.  You might have to open up the permissions a little bit, or add an ACL that allows ftp to have access to the folder.

---

### Post by Lars Noodén on 2009-10-31
> **dm1tr1y said:**
> 
My goal is to configuge simple LAMP server with FTP support. I want to put my PHP files into Apache WWW root using FTP.


Thanks.  But while that names protocols and other specifics, it does give some general information: you want to be able to put files and scripts on the web server for publication.  

The two *easy* and secure options would be either SFTP (a completely different protocol from FTP and FTPS) or WebDAV over HTTPS.  Of those two, the one with the fewest steps is SFTP.  I'll describe that. If FTP is a mandatory requirement in the project specifications, say so directly please.

1) Make a group for those who should have write access to the web site, e.g.
[INDENT][FONT="Courier New"]wwwauthors[/FONT][/INDENT]
and add the appropriate users to that group

2) Correct the access permissions for the web server's document root.
e.g.
# set group ownership
[INDENT][FONT="Courier New"]sudo chgrp -R /var/www wwwauthors;[/FONT][/INDENT]

# set directory permissions, 
# sgid means files created there will belong to that group
[INDENT][FONT="Courier New"]find /var/www -type d -exec chmod  u=rwx,g=srwx,o=rx {} \;[/FONT][/INDENT]

# set file permissions
[INDENT][FONT="Courier New"]find /var/www -type f -exec chmod  u=rw,g=rw,o=r {} \;[/FONT][/INDENT]


3) Install OpenSSH-server package

4) Update the server configuration (sshd_config) to limit access to only the document root.  Something like the following goes at the end

```

Match Group wwwauthors
        PasswordAuthentication yes
        ChrootDirectory /var/www


```

From a user perspective, the sftp client will operate much like an ftp client.  The connection of course is encrypted, including password, username and data.

---

### Post by dm1tr1y on 2009-10-31
Grim76, Lars Noodén, thank you for your answers.

But its really mandatory requirement to use FTP for publishing web documents :(

I've tryed to change directory permissions: "sudo chmod 777 /var/www", but after this FTP server termineted anonymous access to it and started to ask me login and password to connect :(

Its VERY strange, because in the FTP server config file - the string "local_enable=YES" is commented!
```
# Uncomment this to allow local users to log in.[FONT=monospace]
[/FONT]#local_enable=YES
```

---

