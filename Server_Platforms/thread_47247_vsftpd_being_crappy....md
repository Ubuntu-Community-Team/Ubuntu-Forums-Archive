---
title: "vsftpd being crappy..."
date: 2005-07-07
forum: Server Platforms
---

### Post by uberlinux on 2005-07-07
I cant get it to disallow anon logons, and allow local logons w/ no chroot, maybe somebody could see what I am doing wrong?
```

listen=YES

background=YES

#

# READ THIS: This example file is NOT an exhaustive list of vsftpd options.

# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's

# capabilities.

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

###not sure if this is needed or possible

log_ftp_protocol=YES

#
#double logging!
dual_log_enable=YES

#this is to change the time from GMT to local

use_localtime=YES

#

#max clients allowed at once 

max_clients=5

#

# You may change the default value for timing out an idle session.

#idle_session_timeout=600

#

# You may change the default value for timing out a data connection.

#data_connection_timeout=120

#

# It is recommended that you define on your system a unique user which the

# ftp server can use as a totally isolated and unprivileged user.

nopriv_user=ftp

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

ftpd_banner=Welcome to .:MoonUnit:.

!!!!WARNING!!!!

It is a Class 3 Felony to access 

this server without express written 

authorization as specified in United

States Statute § 4.01.2  All sessions 

are logged.

#

pasv_min_port=49152

pasv_max_port=51200



secure_chroot_dir=/usr/local/share/vsftpd/empty

```

---

### Post by Phineas on 2005-07-08
[QUOTE=uberlinux]I cant get it to disallow anon logons, and allow local logons w/ no chroot, maybe somebody could see what I am doing wrong?
```

listen=YES

background=YES

#

# READ THIS: This example file is NOT an exhaustive list of vsftpd options.

# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's

# capabilities.

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

###not sure if this is needed or possible

log_ftp_protocol=YES

#
#double logging!
dual_log_enable=YES

#this is to change the time from GMT to local

use_localtime=YES

#

#max clients allowed at once 

max_clients=5

#

# You may change the default value for timing out an idle session.

#idle_session_timeout=600

#

# You may change the default value for timing out a data connection.

#data_connection_timeout=120

#

# It is recommended that you define on your system a unique user which the

# ftp server can use as a totally isolated and unprivileged user.

nopriv_user=ftp

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

ftpd_banner=Welcome to .:MoonUnit:.

!!!!WARNING!!!!

It is a Class 3 Felony to access 

this server without express written 

authorization as specified in United

States Statute § 4.01.2  All sessions 

are logged.

#

pasv_min_port=49152

pasv_max_port=51200



secure_chroot_dir=/usr/local/share/vsftpd/empty

```[/QUOTE]
 Did you restart vsftpd? Your conf file looks right.

---

### Post by uberlinux on 2005-07-08
yup, this always happens to me...

---

### Post by kirsche on 2005-07-16
are you starting the ftp server via inet?
had a problem once as well -  try starting it without inet.

---

### Post by uberlinux on 2005-07-18
[QUOTE=kirsche]are you starting the ftp server via inet?
had a problem once as well -  try starting it without inet.[/QUOTE]
No, I had it as a standalone daemon, I have a shadowed password file if that makes a difference,

---

### Post by kirsche on 2005-07-19
had the same server up and running here before I switched to proftpd.
Check out this page, it might give you a hint...

[http://www.nslu2-linux.org/wiki/Unslung/Vsftpd](http://www.nslu2-linux.org/wiki/Unslung/Vsftpd)

---

### Post by [pl]ice on 2005-07-22
hey, i tested just now ur config. um, bit strange,are you using latest vsftpd???
   it works with mine, strange that you can login with anonymous!!! hm, local user works, anonymous denied (after it checks in passwd), with no chroot() jail enabled.
  posting your config (i changed some bits)
Default: /var/run/vsftpd  ; i disabled your secure_chroot_dir 
yeh, you might want to watch for pidof vsftpd, couse when i was testing mine conf, it came out that i had couple of vsftpd running... no good.
  
> 
listen=YES

background=YES

#

# READ THIS: This example file is NOT an exhaustive list of vsftpd options.

# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's

# capabilities.

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

###not sure if this is needed or possible

#log_ftp_protocol=YES

#
#double logging!
dual_log_enable=YES

#this is to change the time from GMT to local

use_localtime=YES

#

#max clients allowed at once

max_clients=5

#

# You may change the default value for timing out an idle session.

#idle_session_timeout=600

#

# You may change the default value for timing out a data connection.

#data_connection_timeout=120

#

# It is recommended that you define on your system a unique user which the

# ftp server can use as a totally isolated and unprivileged user.

#nopriv_user=ftp

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

#ftpd_banner=Welcome to .:MoonUnit:.

#!!!!WARNING!!!!

#It is a Class 3 Felony to access

#this server without express written

#authorization as specified in United

#States Statute § 4.01.2  All sessions

#are logged.

#

pasv_min_port=49152

pasv_max_port=51200



#secure_chroot_dir=/usr/local/share/vsftpd/empty 

if doesn't work then will post you mine.
bie

---

