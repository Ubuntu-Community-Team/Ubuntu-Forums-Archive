---
title: "vsftpd stops working randomly"
date: 2010-11-29
forum: Server Platforms
---

### Post by Servious on 2010-11-29
On a whim vsftpd seems to stop working randomly and any attempted connection times out while waiting for the welcome message.

It'll take a couple reboots and a couple "sudo service vsftpd restart" 's and it'll eventually start working again.

AFIIK everything is at the most currant version. It just started doing this a few weeks ago.

Here is my config file:
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
dirmessage_enable=NO
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
idle_session_timeout=1200
#
# You may change the default value for timing out a data connection.
data_connection_timeout=1200
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
#ftpd_banner=
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
rsa_cert_file=/etc/ssl/private/vsftpd.pem

```

For the life of me I can't figure out what would cause it to randomly stop working. The line is staying up. I have an IRC bot on this same box and it never disconnects from the server/channel.

Any help would be greatly appreciated.

---

### Post by WinstonChurchill on 2010-11-29
> **Servious said:**
> On a whim vsftpd seems to stop working randomly and any attempted connection times out while waiting for the welcome message.

It'll take a couple reboots and a couple "sudo service vsftpd restart" 's and it'll eventually start working again.

AFIIK everything is at the most currant version. It just started doing this a few weeks ago.

Is the vsftpd process dying? Or does it keep running and just not accept connections? What client are you using to connect? What does vsftpd log when it hangs? What sort of firewalling does you server have?

Also, is there some specific reason you're using the "connect_from_port_20" option? Most clients will expect PASV, and some might not work with port 20 at all.

---

### Post by Servious on 2010-11-29
> **WinstonChurchill said:**
> Is the vsftpd process dying? Or does it keep running and just not accept connections? What client are you using to connect? What does vsftpd log when it hangs? What sort of firewalling does you server have?

Also, is there some specific reason you're using the "connect_from_port_20" option? Most clients will expect PASV, and some might not work with port 20 at all.

The process stays running. I'm using FileZilla to connect (It's never had an issue before) 
The log just says CONNECT and gives the IP then nothing afterwords

UFW - which i know is just IP tables and not a firewall. So everything should be very open for it.

I will attempt to turn off the port 20 thing but it's always been like that. Also my FTP client does work on occasion. So would that really be making it not work intermittently?

---

### Post by Servious on 2010-11-29
Changing the port 20 setting didn't help anything. I was working about 2 hours ago and once again it is suddenly timing out or refusing connections even though the web server and the IRC bot are both up and working flawlessly.

---

### Post by kevinthecomputerguy on 2010-11-30
Try commenting these out and restarting (most likely the top one)
use_localtime=YES
idle_session_timeout=1200
data_connection_timeout=1200

---

### Post by WinstonChurchill on 2010-11-30
> **Servious said:**
> Changing the port 20 setting didn't help anything. I was working about 2 hours ago and once again it is suddenly timing out or refusing connections even though the web server and the IRC bot are both up and working flawlessly.
Have you tried some different clients? Try connecting with Firefox and some others.

---

### Post by billschu on 2010-12-03
I have the same issue - tried commenting out use_localtime=YES
no joy
idle_session_timeout and data_connection_timeout are commented out by default on vsftpd 2.2.0

my issue began when I added a nightly reboot of the vsftpd server - here's my setup:
routing via iptables and dnsmasq on a ubuntu 9.10 desktop
vsftpd in question on a different 9.04 server
connections from winxp-filezilla and ubuntu10.04-gftp sometimes work, usually don't on first attempt in the AM after server reboots
both clients resolve to IP and report successful connection and timeout before the vsftpd welcome message
with no changes a second attempt with the gftp client works fine and then both clients work fine the rest of the day

I've disabled ipv6 on both servers - also with no joy

I don't usually use it, but there is an ancient ubuntu 8.04 vsftpd-version 2.0.6 on the same network that connects fine everytime 

I looked at the vsftpd changelog and there didn't seem to be anything applicable moving to the latest vsftpd version but I'll probably try that next or put up a 10.10 server but I'd really be grateful for any pointers on what to look at next and/or what possible explanation(s) for this intermittent issue is

TIA
Cheers,

---

### Post by inphektion on 2010-12-04
force the filezilla client to not use pasv and see if that works.  that's not a solution but it would be helpful in diagnosing the issue here.
in filezilla for the connection click on the transfer settings tab and under transfer mode select active.

---

### Post by WinstonChurchill on 2010-12-04
Try running this: ```
sudo modprobe ip_conntrack_ftp
```

---

### Post by billschu on 2010-12-08
Solved,
nf_conntrack_ftp already set in iptables

Connecting with client forced to active mode solved the issue - but I don't want the client to need to know they need to force to an active connection

Although vsftpd has pasv support enabled by default i added host name resolution and limited the ports to 51000-51999.  I don't THINK the host name resolution was the problem but one of the two changes fixed the problem and they both seem like good things.  I also don't THINK I'm blocking ports in iptables but with the immediate issue resolved figuring that out will have to wait for another day.

Thanks very much for pointing me in the active vs passive direction.

Cheers,

---

