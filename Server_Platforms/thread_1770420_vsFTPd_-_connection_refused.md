---
title: "vsFTPd - connection refused?"
date: 2011-05-29
forum: Server Platforms
---

### Post by flowevd on 2011-05-29
Hi,

I'm on 10.04 LTS Server Edition and I have an FTP problem I don't understand. Very grateful for any help.

Connecting remotely through FileZilla works ok, but I can't connect from localhost (FWIW I'm running WordPress and would like to be able to upload plugins from the dashboard).

I've got vsFPTPd installed and - I think - running:

```

#  service vsftpd start
vsftpd start/running, process 25782

``` 

All ok so far... however I can't see it on any of my ports:

```

# nmap localhost
Not shown: 995 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
3306/tcp open  mysql

```

And of course if I

```

telnet localhost:21 
```

That's 'Connection refused...'

Nothing in 'netstat --listen' either.

The odd thing is, I can connect fine using FileZilla. 

To confirm, I have 

```
local_enable=YES
```

set in my vsftpd.conf. 

Thanks for any help!

---

### Post by ruffEdgz on 2011-05-30
Just as a side note: **local_enable** is a option for vsftpd to allow local users on the box to login to vsftpd and not about using localhost.

If you are using the option **listen_address** in your configuration, I would just comment that out and restart. That should make vsftpd listen to all interfaces (including localhost) on your server.

Hope that helps.

---

### Post by flowevd on 2011-05-30
Hi ruffEdgz,

Thanks for your suggestion, but I haven't got that option set. Any other ideas?

---

### Post by ruffEdgz on 2011-05-30
Just some other questions:
---
* When you say it works for Filezilla, what host are you providing there? 
* Localhost and it works? 
* Is the Filezilla installed on the same machine as the vsfstd server for your test?
* Can you share your vsftpd.conf file with us on your next post?
---
Seems odd that if you aren't bypassing your localhost if you didn't tell it to within your vsftpd.conf file so the more information we can have about your setup and testing, the better we can provide help.

---

### Post by flowevd on 2011-05-30
Thanks for your help.

In FileZilla, I'm using the IP address of the server from a remote box. it seems only to work on port 22, which is the ssh port as above.

Nothing seems to work on localhost.

Below is my vsftpd.conf as requested.

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
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users

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
rsa_cert_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

```

---

### Post by ruffEdgz on 2011-05-30
So here is what I found in that config file that is being used:
```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users

secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES

```
I see that you are forcing SSL which will only use port 22. The service is working the way it is configured at this time.

So I'm guessing the question now turns to: "Can I use both port 21 and port 22 as connection options for vsftpd?" I don't see why not but some changes will need to be made to the **force_local_data_ssl** and **force_local_logins_ssl** most likely. You may also need to add additional options to the configuration like **listen_port** having both 21 and 22 to listen to. It becomes more of a security question for you to answer since opening up port 21 will be insecure for data and logins. I have only done the SFTP configuration for vsftpd so I'm not a fan about opening port 21.

Hope this helps.

---

### Post by flowevd on 2011-05-31
Thanks very much for your help - this is clear now. I've loosened the settings to not require SSL as you suggest. I tried opening port 21 to check that worked but couldn't see it - then i realise it doesn't even seem to be running!

```
# service vsftpd start
vsftpd start/running, process 26098

```

but immediately afterwards...

```
# service vsftpd stop
stop: Unknown instance:

```

i wonder why this is?

---

