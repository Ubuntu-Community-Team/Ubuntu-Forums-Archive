---
title: "Server set up for newbie: samba, proftpd and mysql"
date: 2010-08-23
forum: Server Platforms
---

### Post by CbIP on 2010-08-23
Hi guys! Finally I decided and installed ubuntu server instead of my Windows server. First of all I'm a little bit shocked. Second everything works fast and "eats" only 250 Mb RAM. Also I installed webmin, but I have some questions. If possible tell me, how to solve them or where to read, how to solve them.

**Samba**
I'd like to have root access to the file system. So I configured one share like this:
```

[general]
...
security = user
...

[rootfs]
	browseable = no
	comment = rootfs
	valid users = root
	only user = yes
	path = /
```
But when I try to connect using my Win 7 I get login/password form again and again. Also how to create share for user 'cbip' with access to /home/cbip and /var/www and anonymous share with access to /home/torrents ?

**ProFtpD**
I was really shocked here :D because I have never configured FTP servers except gene6ftp. An attempt to configure it using webmin wasn't succesful.
All I need is to make 3 accounts: anonymous with access to /home/ftp/public, login:password with access to /home/login and /home/ftp/privte and login1:password1 with access to /var/www

**MySQL**
I am not shocked any more, but I need to restrict user 'cms' from access to 'information_schema' tables...

Thank you very much for your help and advice!

---

### Post by maikel.b on 2010-08-23
Hello, i will help you with samba, 

First add the user root in samba

smbpasswd -a root

give password
give password

Oke user for samba is set.

edit your /etc/samba/smb.conf 

with this.

[rootfs]
        browseable = yes
        comment = rootfs
        valid users = root
        path = /

restart the samba server.
and also reboot or logout with windows, and try to login again with the password you give to root..

When you cant find your samba share use the ip-addresses like this
\\192.168.1.40  This for microsoft browser...

use the ipadress of your own server...

Access the map rootfs

User name = root
password for the root user.  ( this is the password you used with smbpasswd -a root )

this should work for the samba section..... 

[COLOR=#000000]success[/COLOR]...

---

### Post by triunenature on 2010-08-23
> **CbIP said:**
> 
**MySQL**
I am not shocked any more, but I need to restrict user 'cms' from access to 'information_schema' tables...

Webmin has tools for that!

Enter webmin 

[https://serverip:10000/](https://serverip:10000/)

go to servers (right panel, half way down)

open mysql database server

under global options, click user permissions

edit his permissions to ... nothing.  unhighlight all his authority.

Problem solved!!

Good luck!

---

### Post by CbIP on 2010-08-24
Thank you very much for your help! MySQL work fine! Samba works fine too, but I have read-only access to files and folders with root account - how to fix it?
Also, I've installed GNOME for configuring proftpd (Gadmin-proftpd), but it seems not to be working properly: when I try to save new settings some of them (username length, password length, HTML statistics) are being restored to default. Also only anonymous virtual user works - I can't login with another user with password. The error is: '530 &#1053;&#1077;&#1082;&#1086;&#1088;&#1088;&#1077;&#1082;&#1090;&#1085;&#1099;&#1077; &#1076;&#1072;&#1085;&#1085;&#1099;&#1077; &#1072;&#1091;&#1090;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1094;&#1080;&#1080;.' (530 Incorrect auth. data)
How to configure it?

My **proftpd.conf**:
```
ModulePath /usr/lib/proftpd
LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c
LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
LoadModule mod_dynmasq.c
LoadModule mod_ifsession.c
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.0.2"
ServerIdent on "CbIP ftp"
ServerAdmin CbIP@bk.ru
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 0
TransferRate STOR 0
TransferRate STOU 0
TransferRate APPE 0
SystemLog /var/log/secure
RequireValidShell off
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser test1234
  DenyALL
</Limit>

<Anonymous /var/www>
User test1234
Group users
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

```

**ls -la /usr/lib/proftpd**
```
-rw-r--r--   1 root root 38728 2009-12-22 13:59 mod_ban.so
-rw-r--r--   1 root root 26460 2009-12-22 13:59 mod_ctrls_admin.so
-rw-r--r--   1 root root  9660 2009-12-22 13:59 mod_dynmasq.so
-rw-r--r--   1 root root 13836 2009-12-22 13:59 mod_facl.so
-rw-r--r--   1 root root 13968 2009-12-22 13:59 mod_ifsession.so
-rw-r--r--   1 root root  9688 2009-12-22 13:59 mod_load.so
-rw-r--r--   1 root root  9644 2009-12-22 13:59 mod_quotatab_file.so
-rw-r--r--   1 root root  5548 2009-12-22 13:59 mod_quotatab_radius.so
-rw-r--r--   1 root root 47708 2009-12-22 13:59 mod_quotatab.so
-rw-r--r--   1 root root 13800 2009-12-22 13:59 mod_quotatab_sql.so
-rw-r--r--   1 root root 43412 2009-12-22 13:59 mod_radius.so
-rw-r--r--   1 root root 22668 2009-12-22 13:59 mod_ratio.so
-rw-r--r--   1 root root 38764 2009-12-22 13:59 mod_rewrite.so
-rw-r--r--   1 root root 13956 2009-12-22 13:59 mod_site_misc.so
-rw-r--r--   1 root root 22492 2009-12-22 13:59 mod_sql_mysql.so
-rw-r--r--   1 root root 68496 2009-12-22 13:59 mod_sql.so
-rw-r--r--   1 root root 98192 2009-12-22 13:59 mod_tls.so
-rw-r--r--   1 root root  9696 2009-12-22 13:59 mod_unique_id.so
-rw-r--r--   1 root root  9672 2009-12-22 13:59 mod_wrap2_file.so
-rw-r--r--   1 root root 22372 2009-12-22 13:59 mod_wrap2.so
-rw-r--r--   1 root root  9640 2009-12-22 13:59 mod_wrap2_sql.so
-rw-r--r--   1 root root 18088 2009-12-22 13:59 mod_wrap.so

```

**modules.conf**:
```
#
# This file is used to manage DSO modules and features.
#

# This is the directory where DSO modules reside

ModulePath /usr/lib/proftpd

# Allow only user root to load and unload modules, but allow everyone
# to see which modules have been loaded

ModuleControlsACLs insmod,rmmod allow user root
ModuleControlsACLs lsmod allow user *

LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c

# Install one of proftpd-mod-mysql, proftpd-mod-pgsql or any other
# SQL backend engine to use this module and the required backend.
# This module must be mandatory loaded before anyone of
# the existent SQL backeds.
#LoadModule mod_sql.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_ldap.c

#
# 'SQLBackend mysql' or 'SQLBackend postgres' directives are required 
# to have SQL authorization working. You can also comment out the
# unused module here, in alternative.
#

# Install proftpd-mod-mysql and decomment the previous
# mod_sql.c module to use this.
#LoadModule mod_sql_mysql.c

# Install proftpd-mod-pgsql and decommen the previous 
# mod_sql.c module to use this.
#LoadModule mod_sql_postgres.c

# Install proftpd-mod-sqlite and decomment the previous
# mod_sql.c module to use this
#LoadModule mod_sql_sqlite.c

# Install proftpd-mod-odbc and decomment the previous
# mod_sql.c moduleto use this
#LoadModule mod_sql_odbc.c

LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_quotatab_ldap.c

# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_quotatab_sql.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
# Install proftpd-mod-pgsql or proftpd-mod-mysql to use this
#LoadModule mod_wrap2_sql.c
LoadModule mod_dynmasq.c


# keep this module the last one
LoadModule mod_ifsession.c
```

Gadmin-proftpd settings (/etc/gadmin-proftpd/settings.conf):
```
certificate_directory /etc/gadmin-proftpd/certs
random_username_length 6 *_**#I can't change this with gadmin-gproftpd**_*
random_password_length 6 *_**#I can't change this with gadmin-gproftpd**_*
randomize_case lower
useradd_homedir_path /var/ftp
html_path /var/www/html/ftp.htm *_**#I can't change this with gadmin-gproftpd**_*
welcome_name welcome.msg
virtual_users on

```

---

### Post by maikel.b on 2010-08-24
Fix the samba with 
 
[FONT=Consolas][SIZE=2][FONT=Verdana][rootfs][/FONT][/SIZE]
[SIZE=2][FONT=Consolas]browseable = yes[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]comment = rootfs[/FONT][/SIZE]
[SIZE=2][FONT=Consolas]valid users = root[/FONT][/SIZE][/FONT]
[COLOR=black]readonly = no[/COLOR]
[FONT=Consolas][SIZE=2][FONT=Verdana]path = /[/FONT][/SIZE]
 
and restart samba server
 
[/FONT]

---

### Post by CbIP on 2010-08-24
**maikel.b** Thank you very much! Samba works perfect now!

---

### Post by maikel.b on 2010-08-24
> **CbIP said:**
> **maikel.b** Thank you very much! Samba works perfect now!
 
 
[SIZE=2][COLOR=black]No thanks, if you have any questions ask them [/COLOR][/SIZE]
 
[COLOR=black][SIZE=2]Is your FTP server working?? Wy you use **proftpd**? [COLOR=#000]you might want to use vsftpd I use it, and it works fine for me. Its not so hard to configure..[/COLOR][/SIZE][/COLOR]
 
 
 
[SIZE=2][COLOR=black]Greetz Maikel[/COLOR][/SIZE]

---

### Post by Lars Noodén on 2010-08-24
> **maikel.b said:**
> [SIZE=2][COLOR=black]...Wy you use **proftpd**?...

"Why FTP?" is a very good question.  We need to start tracking down where the idea to add FTP to a server comes from and updating those old pages.  

Logins via FTP, and thus the data accessible there, will not be secure.  

Also, OpenSSH Server is already present presumably and that has SFTP already set up for you.  You have of course the text based sftp client, but if you want a GUI, there is SFTP support in most of the file managers (Nautilus, Konqueror, etc) or you can add a special client like FileZilla.

---

### Post by maikel.b on 2010-08-24
> **Lars Noodén said:**
> "Why FTP?" is a very good question. We need to start tracking down where the idea to add FTP to a server comes from and updating those old pages. 
 
Logins via FTP, and thus the data accessible there, will not be secure. 
 
Also, OpenSSH Server is already present presumably and that has SFTP already set up for you. You have of course the text based sftp client, but if you want a GUI, there is SFTP support in most of the file managers (Nautilus, Konqueror, etc) or you can add a special client like FileZilla.
 
 
vsftp can't be secure??!!
 
take a look here on this site..
 
[http://mb.homelinux.net/linuxsite/node/187](http://mb.homelinux.net/linuxsite/node/187)
 
Greetz Maikel.

---

### Post by linux-hack on 2010-08-24
@CbIP :

Isn't it a big security risk to do such a shared folder ? why not use ssh ?

---

### Post by CbIP on 2010-08-24
Yes, I understand. This is a temporary decision. I have to copy a lot of files to a lot of shares - thats why I use root access to all file system. I will disable it as soon as finish.
All I need from FTP server:
[LIST]
[*]anonymous access to /home/ftp/public and upload rights to /home/ftp/public/upload
[*]user:'password read/write access to /var/www                                        # Hereinafter I used ' symbol to disable smile: :p
[*]user2:'password2 full access to it's home directory
[*]user3:'password3 full access to it's home directory and /var/www
[/LIST]
If it is possible to set up the vsftp server this way, please tell me how - I will use it! :)

---

### Post by Lars Noodén on 2010-08-24
> **maikel.b said:**
> {snip}ftp can't be secure??!! 

FTP cannot be secure.  Take a look at [RFC 959](http://tools.ietf.org/html/rfc959)  

The protocol and the programs that use the protocol are separate topics.  
vsftp and proftp are fine for what they do, but they still do FTP and not SFTP.  The can wrap FTP inside SSL, but that is more complex and nominally less secure that SFTP.  

If you are doing uploads, then SFTP is the right choice, and thereby one of the SSH / SFTP servers.
.  
If you are doing anonymous, read-only downloads then one of the choices can be FTP, and thereby one of the FTP servers like vsftp and proftp.

---

### Post by Lars Noodén on 2010-08-24
[LIST]
[*]anonymous access to /home/ftp/public --> Anonymous FTP, HTTP, or Torrent
[*]upload rights to /home/ftp/public/upload --> SFTP
[*]user:'password read/write access to /var/www  --> SFTP    
[*]user2:'password2 full access to it's home directory --> SFTP
[*]user3:'password3 full access to it's home directory and /var/www --> SFTP
[/LIST]

Ok.  That first one could be [Anonymous FTP](http://tools.ietf.org/html/rfc1635) (via vsftp or proftp), HTTP, or Torrent.  Is there a tool that your visitors use that require FTP?  Maybe you already have a torrent running and can use that.   

The easy, fast way to do the others is SFTP.  Users 2 and 3 must have [write permissions](http://www.dartmouth.edu/~rc/help/faq/permissions.html) to /var/www, so they must be in the same group and that [group must have write permission](http://www.library.yale.edu/wsg/docs/permissions/sgid.htm) to /var/www 

The Dartmouth link above mentions ACLs in the context of AFS at the tail end.  (Must have a non-fake IT dept to host AFS!)   EXT, the default file system for Ubuntu, has the ability to use ACLs.  Use them if you need to give different permissions to more than one group per directory.

---

### Post by maikel.b on 2010-08-24
> **CbIP said:**
> Yes, I understand. This is a temporary decision. I have to copy a lot of files to a lot of shares - thats why I use root access to all file system. I will disable it as soon as finish.
All I need from FTP server:
[LIST]
[*]anonymous access to /home/ftp/public and upload rights to /home/ftp/public/upload
[*]user:'password read/write access to /var/www                                        # Hereinafter I used ' symbol to disable smile: :p
[*]user2:'password2 full access to it's home directory
[*]user3:'password3 full access to it's home directory and /var/www
[/LIST]
If it is possible to set up the vsftp server this way, please tell me how - I will use it! :)


It's now 0:17 in Holland tomorrow 19:30 i post the solution for you with vsftpd.. good night greets maikel

---

### Post by maikel.b on 2010-08-25
> **CbIP said:**
> Yes, I understand. This is a temporary decision. I have to copy a lot of files to a lot of shares - thats why I use root access to all file system. I will disable it as soon as finish.
All I need from FTP server:
[LIST]
[*]anonymous access to /home/ftp/public and upload rights to /home/ftp/public/upload
[*]user:'password read/write access to /var/www                                        # Hereinafter I used ' symbol to disable smile: :p
[*]user2:'password2 full access to it's home directory
[*]user3:'password3 full access to it's home directory and /var/www
[/LIST]
If it is possible to set up the vsftp server this way, please tell me how - I will use it! :)

Oke sorry for my late answer, here is the solution for your configuration with vsftpd
I use ubuntu 9.10 and vsftpd version 2.2.0 is the standard and ssl won't work with 2.2.0 version so i got the solution for you without ssl oke if you use ubuntu 10.4 you can use vsftpd with ssl...

here we go......


    apt-get install vsftpd

Install apache only when you haven't done this!!!!?!?!?!? 

apt-get install apache2   optional!!!!!
  
Backup your original vsftpd.conf file
   
  mv /etc/vsftpd.conf /etc/vsftpd.conf-backup
   
  vi /etc/vsftpd.conf
  

#And add this in your vsftpd.conf file!!
   
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
  # Run standalone? vsftpd can run either from an inetd or as a standalone
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
  #anon_root this is the upload for anonymous users
  anon_root=/home/ftp
  #anon umask
  anon_umask=000
  # anonymous enable delete files
  anon_other_write_enable=YES
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
  # in your local time zone. The default is to display GMT. The
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
  # You may restrict local users to their home directories. See the FAQ for
  # the possible risks in this before using chroot_local_user or
  # chroot_list_enable below.
  chroot_local_user=YES
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
  # default. These settings are more Debian-friendly.
  #
  # This option should be the name of a directory which is empty. Also, the
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
  [COLOR=black][FONT=&quot]pasv_min_port=30000[/FONT][/COLOR]
  [COLOR=black][FONT=&quot]pasv_max_port=30100[/FONT][/COLOR]
#end of file vsftpd.conf   
   
  service vsftpd restart
   
   
  Oke from now we make the directory’s users and user access to folders and groups
   
  mkdir -p /home/ftp/public
  chown root.root /home/ftp
  chmod 555 /home/ftp
  chown ftp.ftp /home/ftp/public/
  useradd –d /var/www/ –s [FONT=Courier]/bin/sh [/FONT]user1
  groupadd upload
  usermod –G upload user1
  useradd –m –s [FONT=Courier]/bin/sh [/FONT]user2
  useradd –d /var/www/ –s [FONT=Courier]/bin/sh [/FONT]user3
  usermod –G upload user3
  useradd –m –s [FONT=Courier]/bin/sh [/FONT]user3-home
  chown root.upload /var/www/
  chmod 775 /var/www/
  passwd user1
  passwd user2
  passwd user3
  passwd user3-home
  
All users have ssh access at this moment... is this oke? so be it..
Disable ssh for these users?? 

usermod -s /bin/csh user1

or user2 3 etc..... no ssh access only ftp... with usermod -s /bin/csh userX

Change the user name for your own names, 



User 3 has 2 login  codes because a ftp server can have only one directory for a user. 
  user anonymous has access in the public directory, can upload and remove directory..
  Disable remove a directory for anonymous?   Remove the anon_other_write_enable=YES in vsftpd.conf
  I hoop this guide will help you for vsftpd.conf if you have questions ask..



Greetz Maikel.b

---

### Post by CbIP on 2010-08-27
Thank you very much for this solution!

---

### Post by CbIP on 2010-08-28
Everything works fine now! Thank you very much!
Can I mount or make some link to a folder so the ftp server could have more than one directory for each user? I mean for example mount or make link /home/ftp to /home/user1 and grant him access to his home directory and /home/ftp?

---

### Post by maikel.b on 2010-08-28
> **CbIP said:**
> Everything works fine now! Thank you very much!
Can I mount or make some link to a folder so the ftp server could have more than one directory for each user? I mean for example mount or make link /home/ftp to /home/user1 and grant him access to his home directory and /home/ftp?


Hello, fine that the solution works for you, the question about that user 2 has access to his home directory and to /home/ftp can't work...

Because vsftpd locks the user in their home directory. 
Create a second account for the user, and make the second directory his home folder, or share the password "account" with the user that needs access the other share..

I hope this works for you..

Greetz maikel.b

---

### Post by CbIP on 2010-08-29
This solution doesn't work for me :( Link 'ln -s /var/www /home/user3' doesn't work for ftp access - I can't follow it.
Also, how to enable hidden files in FTP?

---

### Post by maikel.b on 2010-08-29
> **maikel.b said:**
> Hello, fine that the solution works for you, the question about that user 2 has access to his home directory and to /home/ftp can't work...

Because vsftpd locks the user in their home directory. 
Create a second account for the user, and make the second directory his home folder, or share the password "account" with the user that needs access the other share..

I hope this works for you..

Greetz maikel.b


ln -s option can't work, read above.

To force hidden files in a ftp server you must enable this in Filezilla go to the tab **server** in filezilla and activate **force showing hidden files**..

If you want user 2 access user 1 with ftp, share the account with password, or add a new user in your system with the default home this user must access also..
This new user needs rights to access this folder and write to this folder, you can edit with usermod the secondary group upload for this user...

Option for you, if you want user 2 access folder of user 1 (user 1 has access to /var/www)

Create a new user user2-www maybe this is a option for your problem..

add the new user with..

useradd &#8211;d /var/www &#8211;s /bin/sh user2-www

add the user to the group upload!!!!!! with

usermod &#8211;G upload user2-www

give the user2-www a password!!!!

passwd user2-www

password for user2-www
password for user2-www

The directory /var/www has **user and group** root.upload this was already done with the install of your ftp server ( this option you used that i give you )

From now the user2-www has access to the directory of user 1 because the user2-www has access to group [COLOR=Red]user2-www[/COLOR] and group [COLOR=Red]upload[/COLOR].

Or you use SFTP, then you can access all, the user has a login **home dir**, and can browse the whole system, and the /var /etc etc etc....

Login with user2-www and you will see the directory /var/www/

I hope this works for you..  greetz maikel.b

---

### Post by CbIP on 2010-09-01
Thanks! Everything works fine! I'm happy now. Thank you all for your help and advices!

---

