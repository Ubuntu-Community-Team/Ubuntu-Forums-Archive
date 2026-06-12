---
title: "LAMP Server with files in ~/public_html"
date: 2007-05-07
forum: Server Platforms
---

### Post by atwright on 2007-05-07
Hi there,

I have setup Ubuntu 6.10 Server on an old machine with apache 2.0.55, php 5.1.6, mysql 4.1, phpmyadmin, webmin, vsftpd etc...

I have also set it up with userdir:```
# UserDir is now a module
UserDir public_html
UserDir disabled root

<Directory /home/*/public_html>
	AllowOverride FileInfo AuthConfig Limit
	Options Indexes SymLinksIfOwnerMatch IncludesNoExec
</Directory>
```

Everything works excellently, except, I seem to have a permissions issue in both my /var/www & ~/public_html folders. I can upload files into these directories but get a 403 Forbidden on html files and```
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/home/andy/public_html/test2.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
``` for php files.

If I chmod the files to 777 they work fine. 

My current thought on the matter is that I should make these folders owned by the www-data group (of which I am now a member) is this the right thing to do? If not what should I do?

Thanks in advance...

---

### Post by Frosty Cold Drink on 2007-05-07
All you need to do is provide the universe read access to the files and read/execute access to the directories. You can change these locally with just about any file manager, or through a decent FTP client.

```
find ~user/public_html -type d -exec chmod 755 {} \;
find ~user/public_html -type f -exec chmod 644 {} \;
```
The permissions 755 (rwxr-x-r-x) and 644 (rw-r--r--) for directories and files respectively are the key here.

---

### Post by atwright on 2007-05-07
Hi Frosty Cold Drink,

Thank you for the fast reply. That's awesome but it still leaves me with the issue that EVERY file I upload will have to be chmod-ed to work (I can't handle doing that all the time--I'll end up going back to my Win2k server)...

Any advice? Is there something I can do to vsftpd (I can't see anything in the config)..?

PS. There seems to be something wrong with the syntax of the commands you gave me```
find ~user/public_html -type d -exec chmod 755 {} \;
find ~user/public_html -type f -exec chmod 644 {} \;
```
I kept getting the error:```
find: missing argument to `-exec'
```
I ran the command manually on the folder and deleted / re-uploaded the files.

Thanks you very much for your time and effort so far :)

---

### Post by Frosty Cold Drink on 2007-05-07
The commands should be fine. Make sure the \; shows up properly when doing a copy and paste.

Assuming everything else in your server config is default, and you are using a local user to do uploads, add this to your vsftpd.conf
```
local_umask=0022
```

---

### Post by atwright on 2007-05-08
Brilliant, it works :)

I'm so happy!!!

Thank you very, very, very much.

:):):):):)

---

### Post by atwright on 2007-05-09
Oops, it almost works.

I just added a new user "cath" and tried to connect with Filezilla via vsftp and it says:```
Status:	Connecting to 192.168.210.56 ...
Status:	Connected with 192.168.***.**. Waiting for welcome message...
Response:	220 Welcome to Andy's FTP service.
Command:	USER cath
Response:	331 Please specify the password.
Command:	PASS ********
Response:	530 Login incorrect.
Error:	Unable to connect!
```
The username and password I entered are both correct. The folder /home/cath is 755 (owned by user: "cath" / group: "users"). The same permissions apply to /home/cath/public_html (though vsftp should be pointing users directly to /home/<username> shouldn't it?)...

---

### Post by Frosty Cold Drink on 2007-05-09
Do you have an FTP users group? Its not uncommon to have a group to which users must belong in order to use the FTP server.

---

### Post by atwright on 2007-05-09
Sadly, no FTP group. Here is a list of my groups:```
root
daemon
bin
sys
adm
tty
disk
lp
mail
news
uucp
man
proxy
kmem
dialout
fax
voice
cdrom
floppy
tape
sudo
audio
dip
www-data
backup
operator
list
irc
src
gnats
shadow
utmp
video
sasl
plugdev
staff
games
users
nogroup
dhcp
syslog
klog
crontab
ssh
andy
lpadmin
scanner
admin
ssl-cert
mysql
postfix
postdrop

```Do you think that what I have described should have worked?

---

### Post by Frosty Cold Drink on 2007-05-10
It should have worked, yes. Assuming your user is set up properly, check your config file for userlist_enable, userlist_deny, userlist_file. These settings could restrict who can log in to the FTP server.

---

### Post by atwright on 2007-05-11
There is no: userlist_enable, userlist_deny or userlist_file as far as I can see...

Here is the config file:```
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
local_umask=0022
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
ftpd_banner=Welcome to Andy's FTP service.
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
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
#
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
force_dot_files=YES
#listen_address=
#hide_file=
#anon_max_rate=
#local_max_rate=
```I did add the user via webmin's System > Users and Groups section (if that makes any difference)...?

---

### Post by Frosty Cold Drink on 2007-05-11
It looks like authentication is handed off to PAM. Check /etc/pam.d/vsftpd . This file will tell you how authentication is handled, and what is required for a user to log in.

It seems like a lot, but once its figured out things will be easier, and you may be glad it works this way.

---

### Post by atwright on 2007-05-12
/etc/pam.d/vsftpd```
# Standard behaviour for ftpd(8).
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers$

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session

@include common-auth
auth    required        pam_shells.so
```
/etc/ftpusers```
# /etc/ftpusers: list of users disallowed FTP access. See ftpusers(5).

root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
nobody
```
It's not denying the "users" group or any specific users. I don't understand ] (*,)

PS. I don't mind it being difficult, I'm trying to learn Linux (how it works, how to control it etc). I am VERY impressed so far... ;)

---

### Post by Frosty Cold Drink on 2007-05-12
The deny thing is just so you can throw in some users that you don't want to connect via FTP no matter what. The default is probably fine, as none of the users you create will be in there.

The only thing I can see at this point that would cause you greif is the shell requirement. If your new user hasn't been given a valid login shell, they won't be able to connect via FTP. If you are using SSH, try and get your new user to connect via SSH. If it works, something weird is going on. If it doesn't, then its likley a bad login shell or still a password issue.

---

### Post by atwright on 2007-05-13
That's gotta be it. I think I assigned here a shell of /bin/false (or /shell/false or whatever it normally is)... Trying to make the system as secure as possible (otherwise I may as well go back to my Win2k web server), I think I may eventually make this machine web accessible.

Will change it tomorrow--AWESOME!

Thank you very much... :):):):)

---

### Post by Frosty Cold Drink on 2007-05-13
> **atwright said:**
> That's gotta be it. I think I assigned here a shell of /bin/false (or /shell/false or whatever it normally is)... Trying to make the system as secure as possible (otherwise I may as well go back to my Win2k web server), I think I may eventually make this machine web accessible.

Will change it tomorrow--AWESOME!

Thank you very much... :):):):)

No problem. Just remember that PAM will let you do some fun things. You could drop the valid login shell requirement and use an "ftpusers" group, which is actually quite common. That way you explicitly state who can and cannot FTP in.

---

### Post by atwright on 2007-05-17
Yep, that sorted it :)

Again, thank you very, very, very much :)

PS. Sorry to keep asking questions but how would I go about changing PAM to group authentication (I'd promise this was the last question but I probably isn't--lol)?

---

### Post by Frosty Cold Drink on 2007-05-17
You'll need to add this line or something similar to /etc/pam.d/vsftpd
```
auth    required    pam_group.so group=ftpusers
```

---

