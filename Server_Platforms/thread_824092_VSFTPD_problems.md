---
title: "VSFTPD problems"
date: 2008-06-09
forum: Server Platforms
---

### Post by Strychnine45 on 2008-06-09
Cant connect with vsftpd

When I first installed it, I could connect and see the remote folders, but couldnt upload or download or change permissions.  

So I tried Proftpd and wu-ftpd, no luck connecting at all.  
Now reinstalled vsftpd and cannot connect at all.

I have tried rebooting, changing config back to default, still no luck connecting.  The server is not running any firewall at all, the router is, but has port 21 forwarded to the server.

I am at wits end, if anyone can help it'd be greatly appreciated. With the amount of time I've spent on this, if someone can help me get the ftp up and running and accepting connection from filezilla on port 21 and I can upload and chmod, I will paypal you 5 bucks.  Thanks


Heres the config

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
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
chmod_enable=YES
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
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
nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
ascii_upload_enable=YES
ascii_download_enable=YES
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

---

### Post by Strychnine45 on 2008-06-09
Anyonehave an idea?

---

### Post by sahwan on 2008-06-10
the most important thing you didnt do

jest add

```
listen=YES
```


then restart vsftpd

```
sudo /etc/init.d/vsftpd restart
```

---

### Post by atoponce on 2008-06-10
If the service is started, and you can see a running process in ps or top, I would suspect AppArmor.  Stop AppArmor, and see if you can't connect:

```
sudo /etc/init.d/apparmor stop
```

---

### Post by cheruvim on 2008-06-22
What about on the machine you're connecting from? any firewall on there?
If so you will have to use pasv mode and set min/max passv ports on the firewall.

The thing is that ftp is a pain if any firewall exists anywhere because it sends the connect request on the default port and then either connects or listens, based on the mode, on a whole slew of other ports.. if your using the PORT mode then the client dictates the port in which case the client has to have all ports > 1023 open to allow for the server to connect.

If you are in passive mode then the server has to have all ports > 1023 open for the client to connect. The way around this is to set the following:
connect_from_port_20=NO
pasv_enable=YES
pasv_min_port=<minimum port number>
pasv_max_port=<max port number>

and then open all ports (inclusive) between min_pasv_port and max_pasv_port.

This way your client just receives a message from the server saying "hey, use this port x for transfers" and then the client connects to port x while the server listens on port x. That's pasv.

Hope that helps.

---

