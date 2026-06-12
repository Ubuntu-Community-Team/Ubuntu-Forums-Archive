---
title: "VSFTPD errors: Server sent passive reply with unroutable address."
date: 2017-07-30
forum: Server Platforms
---

### Post by nightraver on 2017-07-30
Hello again my Ubuntu friends! Coming to you with a bit of a conundrum. I have, for the last 2 days or so, been trying to get FTP set up on a VM instance of Ubuntu. Needless to say, this process has been equitable to walking on a field of landmines, from missing arguments in the vsftpd config file, to firewall nightmares, it's not been easy; though from what I've been reading on the countless forums out there, I certainly am not alone in this.

So, here's my issue (or the most recent issue anyway):

I have my vsftpd service set up and successfully running on my server instance, perfectly accessible through LAN in both port and passive mode. Everything works out just dandy.

However, upon wandering out of my LAN and past my PFSense firewall, I find things absolutely impossible to access. As it stands now, when I run my server in Active mode and try to access from LAN, I get the following error responses from my server:

```
Status:	Connecting to [SERVER IP-OMITTED]:21...Status:	Connection established, waiting for welcome message...
Status:	Insecure server, it does not support FTP over TLS.
Status:	Server does not support non-ASCII characters.
Status:	Logged in
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/home/[FTP-USER-OMITTED]" is the current directory
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PORT 10,1,10,[LAST-PORT-OMITTED],192,31
Response:	500 Illegal PORT command.
Command:	PASV
Response:	550 Permission denied.
```

From what I have been reading online, this is caused by issues relating to active FTP over NAT (which PFSense, again my router, does). Soooo... advice was to set the FTP server to passive.

Soooo... because for some reason the vsftpd.conf file is somehow incomplete in Ubuntu's latest distro, I have had to add, among other things like the custom port field, all the pasv_enable fields.

Below is my config file for vsftpd as it is configured now:

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
listen=NO
#
# This directive enables listening on IPv6 sockets. By default, listening
# on the IPv6 "any" address (::) will accept connections from both IPv6
# and IPv4 clients. It is not necessary to listen on *both* IPv4 and IPv6
# sockets. If you want that (perhaps because you want to listen on specific
# addresses) then you must run two copies of vsftpd with two configuration
# files.
listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default).
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
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
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
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO


#
# Uncomment this to indicate that vsftpd use a utf8 filesystem.
#utf8_filesystem=YES
pasv_enable=YES
pasv_max_port=10500
pasv_min_port=10800
pasv_address=[SERVER IP-OMITTED]

```

As you can see above, the pasv mode has been set and given it's pasv range as well as the external IP of my server host (yes it is set, trust me). Still, I receive the dreaded: *"Server sent passive reply with unroutable address. Using server address instead." *error message.

I am stuck here atm. From what I'm gathering on many different forums, NAT is to blame. But from what I'm seeing, this issue should have been solved by entering the pasv_address field.

Any help can be appreciated here!

Hope to hear from you soon!

---

### Post by darkod on 2017-07-31
Is it an option for you to use sftp or scp? They both work over standard ssh port 22 and is easy to allow through a firewall. Plus the communication is very secure unlike ftp.
Ftp should really be avoided whenever you can.

---

### Post by nightraver on 2017-07-31
I can technically use SFTP, and am eventually going to be utilizing it for our purposes. I was just using standard ftp for testing purposes, but I feel that it might be easier than regular ftp?

---

