---
title: "Problem in vsftpd: Anonymous User Access"
date: 2005-10-22
forum: Server Platforms
---

### Post by jhumbo on 2005-10-22
I'm trying to get anonymous user access to work with vsftpd, but I cannot get vsftpd to show the files in the home directory.  Configuration and documentation is as follows:

vsftpd.conf [
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
idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
# The default is nobody.
nopriv_user=nobody
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
ascii_upload_enable=YES
ascii_download_enable=YES
#
# You may fully customise the login banner string:
ftpd_banner=Welcome to the LUCIN Mainframe.
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
ls_recurse_enable=YES


listen=YES
anon_other_write_enable=YES
download_enable=YES

no_anon_password=YES

chroot_local_user=YES
passwd_chroot_enable=YES

text_userdb_names=YES

use_localtime=YES

anon_root=/var/ftp/pub
#local_root=/var/ftp

pasv_min_port=62000
pasv_max_port=63000

anon_world_readable_only=NO

ftp_username=ftp
]

Anonymous login example [
# ftp localhost
Connected to localhost.localdomain.
220 Welcome to the LUCIN Mainframe.
Name (localhost:root): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
226 Transfer done (but failed to open directory).
ftp>
]

User login example [
# ftp localhost
Connected to localhost.localdomain.
220 Welcome to the LUCIN Mainframe.
Name (localhost:root): webserver
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
200 PORT command successful. Consider using PASV.
150 Here comes the directory listing.
drwxr-xr-x    2 0        0            4096 Oct 17 12:57 apache2-default
226 Directory send OK.
ftp>
]

passwd [
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/bin/sh
bin:x:2:2:bin:/bin:/bin/sh
sys:x:3:3:sys:/dev:/bin/sh
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/bin/sh
man:x:6:12:man:/var/cache/man:/bin/sh
lp:x:7:7:lp:/var/spool/lpd:/bin/sh
mail:x:8:8:mail:/var/mail:/bin/sh
news:x:9:9:news:/var/spool/news:/bin/sh
uucp:x:10:10:uucp:/var/spool/uucp:/bin/sh
proxy:x:13:13:proxy:/bin:/bin/sh
www-data:x:33:33:www-data:/var/www:/bin/sh
backup:x:34:34:backup:/var/backups:/bin/sh
list:x:38:38:Mailing List Manager:/var/list:/bin/sh
irc:x:39:39:ircd:/var/run/ircd:/bin/sh
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/bin/sh
nobody:x:65534:65534:nobody:/nonexistent:/bin/sh
dhcp:x:101:101::/nonexistent:/bin/false
syslog:x:102:102::/home/syslog:/bin/false
klog:x:103:103::/home/klog:/bin/false
michael:x:1000:1000:Michael Lucin,,,:/home/michael:/bin/bash
cupsys:x:100:104::/:/bin/false
fetchmail:x:104:65534::/var/run/fetchmail:/bin/sh
messagebus:x:105:110::/var/run/dbus:/bin/false
hal:x:111:111:Hardware abstraction layer,,,:/var/run/hal:/bin/false
saned:x:112:112::/home/saned:/bin/false
gdm:x:106:113:Gnome Display Manager:/var/lib/gdm:/bin/false
hplip:x:107:7:HPLIP system user,,,:/var/run/hplip:/bin/false
ftpuser:x:1001:1001::/dev/null:/etc
trustedftp:x:1003:1003::/var/ftp:/bin/bash
ftp:x:1004:100::/var/ftp/pub:
webserver:x:1005:1004::/var/www:/bin/bash
]

Permissions [
# ls -ald /var/ftp
drwxrwxrwx  3 ftp ftpgroup 4096 2005-10-18 14:43 /var/ftp
# ls -ald /var/ftp/pub
dr--r--r--  3 ftp ftpgroup 4096 2005-10-22 02:10 /var/ftp/pub
# ls -ald /var/ftp/pub/incoming
drw-rw-rw-  2 ftp ftpgroup 4096 2005-10-18 15:08 /var/ftp/pub/incoming
# ls -ald /var/www
drwxr-xr-x  3 root root 4096 2005-10-22 03:00 /var/www
]

Any help will be much appreciated.  I'm sorry for posting such a large message.  I will try and let you know of any additional information by request.  Thank you again.

jhumbo

EDIT:  I have found that enabling Execute access, I am able to successfully use anonymous ftp.  Must Execute access be granted to allow anonymous usage?  (Is there another way?)  Is this a security risk?

---

### Post by supergrapeman on 2005-10-22
[QUOTE=jhumbo]I'm trying to get anonymous user access to work with vsftpd, but I cannot get vsftpd to show the files in the home directory.  Configuration and documentation is as follows:

[stuff snipped]

Any help will be much appreciated.  I'm sorry for posting such a large message.  I will try and let you know of any additional information by request.  Thank you again.

jhumbo

EDIT:  I have found that enabling Execute access, I am able to successfully use anonymous ftp.  Must Execute access be granted to allow anonymous usage?  (Is there another way?)  Is this a security risk?[/QUOTE]

I think it is required, for files to be visible.

Of course, this position is less secure than not allowing anonymous users to see that files exist.

The bigger security issue which you have is that you are allowing anonymous ftp'ers to write. Tread carefully!

---

### Post by jhumbo on 2005-10-22
Alrighty, thank you very much.  I think I got it all up and working alright, but we'll have to see after some testing.  To clarify in case anybody else has this problem, I had to enable execute access on the folders to give the ftp user the ability to view the contents.  Thank you for the help.

jhumbo

---

