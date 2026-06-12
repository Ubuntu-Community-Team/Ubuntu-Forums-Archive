---
title: "vsftpd: unable to connect"
date: 2012-04-19
forum: Server Platforms
---

### Post by chimpsky123 on 2012-04-19
Hi There,
 
[FONT=Times New Roman][SIZE=3]I’ve been banging my head against the wall trying to get vsftpd to work on my Ubuntu 11.10 box. The issue is that I cannot establish a connection. If I try to connect from localhost, I get a “530 Login incorrect” error after I enter the password. /var/log/vsftpd.log shows:[/SIZE][/FONT]
 
```
 
CONNECT: Client "127.0.0.1"
[userftp] FAIL LOGIN: Client "127.0.0.1" 

```
[FONT=Times New Roman][SIZE=3]Here are the contents of my /etc/vsftpd.conf file:[/SIZE][/FONT]
```
 
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem

```
[FONT=Times New Roman][SIZE=3]The ‘userftp’ user is not listed in /etc/ftpusers. Here is the entry from /etc/passwd:[/SIZE][/FONT]
```
 
userftp:x:1003:1003::/var/www:/bin/false

```
[FONT=Times New Roman][SIZE=3]BTW, /bin/false is listed in /etc/shells. Here are the contents of /etc/pam.d/vsftpd:[/SIZE][/FONT]
```
 
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
@include common-account
@include common-session
@include common-auth
auth    required        pam_shells.so

```
[FONT=Times New Roman][SIZE=3]I did make sure the service was running:[/SIZE][/FONT]
```
 
ps -ef | grep vsftpd
root     28572     1  0 21:10 ?        00:00:00 /usr/sbin/vsftpd

```
[FONT=Times New Roman][SIZE=3]I’ve even purged/installed vsftpd, and I made certain there aren’t any funny characters in userftp’s password (just a-Z and 0-9). [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Any ideas why I can’t establish an ftp connection?[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]Thanks, [/FONT][/SIZE]

---

### Post by wojox on 2012-04-19
Take a look here [Install Vsftpd]("http://www.server-world.info/en/note?os=Ubuntu_11.04&p=ftp&f=1")

---

### Post by for.i.am.root on 2012-04-19
When I set up vsftpd on my rig (10.04 x64) I had problems using /bin/false (I assume) due to the login shell. Changed it to bash and have had no problems. Worked immediately.

I then changed it to only allow local and to use ssh with port bindings and RSA keys.

In other words try changing the shell. Worked for me.

---

### Post by chimpsky123 on 2012-04-19
[FONT=Times New Roman][SIZE=3]@for.i.am.root[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Thanks for the input, but I’m still seeing the same behavior. [/SIZE][/FONT]
 
```
 
User1@host:~$ sudo usermod userftp -s /bin/bash
User1@host:~$ cat /etc/passwd | grep userftp
userftp:x:1003:1003::/var/www:/bin/bash

```
```
 
User1@host:~$ ftp localhost
ftp: connect to address ::1: Connection refused
Trying 127.0.0.1...
Connected to localhost.
220 (vsFTPd 2.3.2)
Name (localhost:User1): userftp
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> bye
221 Goodbye.

```
[FONT=Times New Roman][SIZE=3]From /var/log/vsftpd.log:[/SIZE][/FONT]
```
 
Wed Apr 18 23:36:55 2012 [pid 2] CONNECT: Client "127.0.0.1"
Wed Apr 18 23:37:06 2012 [pid 1] [userftp] FAIL LOGIN: Client "127.0.0.1"
 

```[FONT=Times New Roman][SIZE=3]@wojox[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]After I changed the shell for userftp I went ahead and included the options recommended in the link, added userftp to the /etc/vsftpd.chroot_list file, restarted the service. However, I’m seeing no change in behavior… you can see why I’m banging my head against the wall [/FONT][FONT=Wingdings][FONT=Wingdings]J[/FONT][/FONT][FONT=Times New Roman]. Below are the full contents of the /etc/vsftpd.conf file. [/FONT][/SIZE]
 
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
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
ls_recurse_enable=YES
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
local_root=/var/www
 

```

---

### Post by for.i.am.root on 2012-04-19
Try using your username and passwo> rd. Might be a username issue.

Your conf files match mine almost exactly and mine works with standard username and pass.

EDIT

Your conf file is set to only allow users access to their home directory through a chroot. In Jaunty those files weren't created until after a local login.

This may be your problem. Try logging in with credentials of a local user. If it works login once through the FTP user which will create the necessary files required to allow that user FTP access.

If 11.10 is not like Jaunty in that respect the problem has to be  in the user management / configuration.

Just tried it on 10.04. Added new user, without logging in ftp'd in. No issues.

---

### Post by chimpsky123 on 2012-04-20
Still no luck... I logged into the host via ssh with the userftp user without any issues. But I can see the same behavior if I try to ftp to localhost from the ssh session:
 
```
 
login as: userftp
userftp@host's password:
Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-14-server x86_64)
 * Documentation:  [https://help.ubuntu.com/11.10/serverguide/C](https://help.ubuntu.com/11.10/serverguide/C)
The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Sun Aug 14 21:13:43 2011 from maple
userftp@host:~$ pwd
/var/www
userftp@host:~$ ftp localhost
ftp: connect to address ::1: Connection refused
Trying 127.0.0.1...
Connected to localhost.
220 (vsFTPd 2.3.2)
Name (localhost:userftp):
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> bye
221 Goodbye.
userftp@host:~$ ps -ef | grep vsftp
root     28821     1  0 Apr18 ?        00:00:00 /usr/sbin/vsftpd
userftp  29878 29818  0 21:56 pts/2    00:00:00 grep vsftp
 

```
...and from /var/log/vsftpd.log:
 
```
 
Thu Apr 19 21:55:06 2012 [pid 2] CONNECT: Client "127.0.0.1"
Thu Apr 19 21:55:13 2012 [pid 1] [userftp] FAIL LOGIN: Client "127.0.0.1"

```
 
I'm really baffled. At this point I'm willing to try a different sftp server; any recommendations?

---

### Post by for.i.am.root on 2012-04-20
That's insane. Works great for me. When I get a chance I will post my relevant conf filed for ya for comparison.

Looks like you can connect just fine you are just unable to authenticate. Really weird.

---

### Post by for.i.am.root on 2012-04-20
> 
I could resolve it . Thanks for your reply. pam entries are missing in my /etc/vsftpd.conf

I added the following entries in vsftpd.conf

pam_service_name=vsftp
userlist_enable=YES

Then I created the /etc/pam.d/vsftpd file by copying from /etc/pam.d/sshd . The following are the contents of my /etc/pamd.d/vsftpd

#%PAM-1.0
auth required pam_stack.so service=system-auth
auth required pam_nologin.so
account required pam_stack.so service=system-auth
password required pam_stack.so service=system-auth
session required pam_stack.so service=system-auth
session required pam_loginuid.so


ftp -d 127.0.0.1 will tell us if it's your authentication.

---

### Post by chimpsky123 on 2012-04-22
Here is the output with the debugging flag:
 
```
 
userftp@host:~$ ftp -dv 127.0.0.1
Connected to 127.0.0.1.
220 (vsFTPd 2.3.2)
ftp: setsockopt: Bad file descriptor
Name (127.0.0.1:userftp):
---> USER userftp
331 Please specify the password.
Password:
---> PASS XXXX
530 Login incorrect.
Login failed.
---> SYST
530 Please login with USER and PASS.
ftp>

```
 
I looked at the post you cited and modified my /etc/pam.d/vsftpd file to match theirs:
```
 
# Standard behaviou for ftpd(8).
#auth   required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed
# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.
# Standard pam includes
#@include common-account
#@include common-session
#@include common-auth
#auth   required        pam_shells.so
auth required pam_stack.so service=system-auth
auth required pam_nologin.so
account required pam_stack.so service=system-auth
password required pam_stack.so service=system-auth
session required pam_stack.so service=system-auth
session required pam_loginuid.so
 

```
 
I then restarted vsftpd, but I didnt see any difference. Although, I'm not certain if there is some other service that needs to be restarted for the changes to the /etc/pam.d/vsftpd file to take effect. 
 
I also tried logging in with another user that I have to perform day to day tasks, but I get the same '530 login incorrect' message. One thing I haven't tried is a full reboot of the host... I may try this as a sanity check.

---

### Post by henrylaw on 2012-05-09
Have any of the posters got any further with this?  I've just installed Precise on a new server I'm building, added vsftpd and am getting these 530 errors, with no explanation anywhere that I can see.  Lots of hits on the net about people getting the problem, and I think there are registered bugs, but nobody seems to have an answer.

I've tried deleting and reinstalling vsftpd twice.  The user/password combination I'm trying in ftp works when I login directly.  Its shell is /bin/bash, which is in the shells list.

Aaaaaagh!

---

### Post by henrylaw on 2012-05-09
I've got further myself.  If I rename /etc/pam.d/vsftpd to something else, login works.  Not a good solution (presumably authentication is damaged in some way) but a pointer to where the problem is.

Now to read up on pam and vsftpd.   Anyone else making/made progress?

---

### Post by henrylaw on 2012-05-09
Maybe I should have done all this before I posted first ...

My /etc/pam.d/vsftpd is, as supplied, this:
```
# Standard behaviour for ftpd(8).
auth    required    pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own. Do not enable pam_ftp.so.

# Standard pam includes
@include common-account
@include common-session
@include common-auth
auth    required    pam_shells.so
```I've found out now that unless I comment out **both** the "auth" statements, the login fails as described earlier. It's as if both those pam modules were failing.  Is the error in PAM, perhaps?  The account I'm using has [FONT=Courier New]/bin/bash[/FONT] as its shell, which is definitely in [FONT=Courier New]/etc/shells[/FONT], so pam_shells.so should be happy; and that user is not in [FONT=Courier New]/etc/ftpusers[/FONT], so pam_listfile.so shouldn't complain either.

Anyway, I have a workround, for the time being.  This server is entirely internal to my network so I'm not too worried about those two PAM modules.

---

### Post by jtupulis on 2012-06-06
btw, initially for me helped to change in /etc/vsftpd.conf:

pam_service_name=vsftpd -> pam_service_name=ftp

to be honest, after installing OpenLDAP i had to change it back, not understanding why... -> I'm still learning :)

---

