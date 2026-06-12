---
title: "VSFTPD unable to Configure to allow users to access via Filezilla client or otherwise"
date: 2015-09-20
forum: Server Platforms
---

### Post by Aphexlog on 2015-09-20
Hello every one,

I am trying to set up VSFTPD on a Linux server and I am unsure as to what configuration is preventing me from connecting from another local computer via a filezilla client (from a windows computer)

I will past the vi text from relevant configuration files, please let me know if you need more information.                 Thank you in advance

[B]VSFTPD.CONF FILE:
[/B][awest@Odin etc]$ sudo vi vsftpd/vsftpd.conf
[sudo] password for awest:
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
#banned_email_file=/etc/vsftpd/banned_emails
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
#chroot_list_file=/etc/vsftpd/chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# When "listen" directive is enabled, vsftpd runs in standalone mode and
# listens on IPv4 sockets. This directive cannot be used in conjunction
# with the listen_ipv6 directive.
listen=NO
#
# This directive enables listening on IPv6 sockets. By default, listening
# on the IPv6 "any" address (::) will accept connections from both IPv6
# and IPv4 clients. It is not necessary to listen on *both* IPv4 and IPv6
# sockets. If you want that (perhaps because you want to listen on specific
# addresses) then you must run two copies of vsftpd with two configuration
# files.
# Make sure, that one of the listen options is commented !!
listen_ipv6=YES


pam_service_name=vsftpd
userlist_enable=YES
tcp_wrappers=YES

[B]Here are my firewall rules (open ports):
[/B]Chain IN_public_allow (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:32400 ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp-data ctstate NEW
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ssh ctstate NEW

---

### Post by mastablasta on 2015-09-21
why not use SSH instead and then sFTP via filezila. it should be safer (keys+password+tunneling) and it is pretty easy to setup.

---

