---
title: "VSFTPD connection problems"
date: 2011-10-24
forum: Server Platforms
---

### Post by algoe on 2011-10-24
Hi!

I'm trying to get VSFTPD running on my server. Right now all I want is to be able log on with local user accounts, and they should be locked in their home folders.


The following problem occurs when i try to connect remotely:
(sensitive information has been removed)
```
martin@labbdator:~$ ftp <server url>
ftp: connect to address <ipv6-adress>: Connection refused
Trying <ipv4-adress>...
Connected to <server url>
220 (vsFTPd 2.2.2)
Name (<server url>:martin): <username>
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
421 Service not available, remote server has closed connection

```

It works fine if i connect locally:
```
martin@<server>:~$ ftp localhost
Connected to localhost.
220 (vsFTPd 2.2.2)
Name (localhost:martin): <username>
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
<correct directory listing>

```

I am running UFW but I tried disabling it without any difference. The server is dual stacked (both IPv4 and v6) but VSFTPD is not configured to listen on v6.

My vsftpd.conf:
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
All that is changed from default is that i uncommented the two following lines: "local_enable=YES" and "chroot_local_user=YES".

The server is running Ubuntu 10.04.3 LTS.
The logs (/var/log/vsftpd.log, messages and syslog) show nothing of value. vsftpd.log states that the client connected and logged in OK.
Various forum threads suggest that the 421 error has to do with problems with user authentication, but in this case the AUTH is successful and also I have no problem when connecting locally.

---

### Post by Jonathan L on 2011-10-24
> **algoe said:**
> I'm trying to get VSFTPD running on my server. Right now all I want is to be able log on with local user accounts, and they should be locked in their home folders.

The following problem occurs when i try to connect remotely:
```
ftp> ls
421 Service not available, remote server has closed connection
```Local
```
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
```

Hi Algoe

To me looks like something is port filtering and doesn't let the data port work; either your server (ie, ufw) or perhaps your router..  I wasn't clear from your post whether the failure is from another machine inside your network (in which case it looks like ufw configuration), or from outside your network and going through your router (could be router or ufw).

FTP has complex port behaviour: when you do a transfer (including ls), one side makes a new data socket, gives the details over the existing (control) socket, and the other side connects to the data socket.  The normal 'active' mode is that the client creates the data socket; you can use passive mode for the server to create it.  To debug this, you need to know exactly what is trying to connect to where.

First thing: get a little more info, by doing 
```
ftp>debug
```Do you get the same result connecting from the server to itself on its ethernet interface?
Try connecting to the server by local ip address (I'll pretend it's 192.168.1.64):
```
$ ftp 192.168.1.64
```And do you get the same behaviour with passive mode?
```
ftp> passive
ftp> ls
```Post the results, we should be able to work it out from those tests.

Hope that's of some use.

Kind regards,
Jonathan.

PS.  You'll need "chroot_local_user=YES" once you have it working.

---

### Post by algoe on 2011-10-24
The failure is from outside my network. The server has two interfaces, one to the internal network and one with a public IP connected to my ISP with just a switch in between (Actually it is a virtual server in virtualbox and the network interfaces are bridged to physical interfaces on the host which is the directly connected, so it's basically the same as a switch from our point of view). The routing works since I have no problems browsing to the website this server is also hosting. When I do route -n I can see that the default route is towards my ISP and not to the internal network (I had this problem earlier).

Debug did give some interesting info:
```
Connected to <blah>
220 (vsFTPd 2.2.2)
Name (<blah>:martin): <username>
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> debug
Debugging on (debug=1).
ftp> ls
ftp: setsockopt (ignored): Permission denied
---> PORT 192,168,1,113,130,134
421 Service not available, remote server has closed connection

```
Does that mean it's trying to use the ports 192,168,1,113,130 and 134? To me that looks a whole lot like an IP-address, 192.168.1.x is very common in private networks. My private network is in the 192.168.15.x space though...

As stated earlier, i rule out UFW since i get the same problem when it is disabled. I have allowed ports 20 and 21.

Here is connecting to the interface address locally:
```
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> debug
Debugging on (debug=1).
ftp> ls
ftp: setsockopt (ignored): Permission denied
---> PORT <edit!>,223,217
200 PORT command successful. Consider using PASV.
---> LIST
150 Here comes the directory listing.
<listing here>
226 Directory send OK.

```

Edit: removed some numbers since i figured my public IP was on display ;) See post below.

---

### Post by algoe on 2011-10-24
Hmmm! I tried connecting from one of the machines on the local network, and that worked! OK, I may have to admit it's network related then.. :)

Edit: OK i see now what i thought was ports is probably the address it thinks I'm connecting from, at least the first 4 numbers. Then it makes sense I have problems when it thinks I'm on 192.168.1.x!

And hey, that's true, the client is on a NATed network, which DOES have the 192.168.1.x.... So, is that really supposed to be the client address there? Shouldn't it at least display the clients external IP?

---

### Post by algoe on 2011-10-24
Google tells me the PORT command is the client telling the server where to connect to if using active mode. But I also read that if that doesnt work, it should default to PASV (passive mode). The search goes on...

Edit: spelling >_<

---

### Post by algoe on 2011-10-24
Aaand we found the problem. When i specifically tell the client to use passive mode it works.
Question remains: how do i "fix" it? Shouldn't the software figure out that active won't work and try to do passive instead?
I've never run into this problem before when setting up vsftpd :confused:

---

### Post by Jonathan L on 2011-10-24
Hi again Algoe

> Does that mean it's trying to use the ports 192,168,1,113,130 and 134?No: It means it's using 192.168.1.113 and port 33414 (130 * 256 + 134).  This port number will change on every connection.  In normal actve mode, the client chooses a port and listens on it, and the server opens a connection to that port.  Good writeup of FTP port behaviour is [http://slacksite.com/other/ftp.html](http://slacksite.com/other/ftp.html)

> And hey, that's true, the client is on a NATed network, which DOES have  the 192.168.1.x.... So, is that really supposed to be the client address  there? Shouldn't it at least display the clients external IP?At the client you will see what the client thinks its address is, ie, pre-NAT.  At the server you'll see what the server thinks the client's address is, ie post-NAT.  FTP is one of the very few protocols where the router doing the NAT has to look inside the packets and change the data.

> I've never run into this problem before when setting up vsftpdIt's nothing to do with VSFTP in particular: this problem is (sadly) common to the protocol.  My only thought is you've been lucky with your network configurations!

> Question remains: how do i "fix" it?You find the router/config which is blocking the server sending the new connection to the high numbered port on your client.  As I said above, this is common to all implementations of FTP, so it's pretty certain you'll be able to find the right part on your router.

Hope that helps, let us know how you get on.

Kind regards
Jonathan.

---

