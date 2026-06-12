---
title: "Lots Newb Questions"
date: 2005-07-26
forum: Server Platforms
---

### Post by Baci on 2005-07-26
I installed ubuntu yesterday, I have sucessfully got apache2 & php to work (that was soo hard, not; thanks synaptic.)

I am trying to setup vsftpd.conf my problem/s are:

I cannot save the file (i figured out how to chmod it so that I could edit it, but now that I can edit it, it won't let me save it) I also see no place in the vsftpd.conf file to make it so non-anon users can login (when i try to connect it says the server is only anon .... wth?)

I'm not bothering posting my config, as its just the default (im trying to edit it.)

After I get the config file problem solved, I am also wondering how I can add users to FTP, currently as I think it works, you have to have a user account, the same one you would use to physically login to the computer, is this just how linux works? I thought you could set up virtual users or something.

My previous server experiance is just windows apache, guildftp (windows), RaidenMAILD (windows) and lots of other windows server crap, though I would like to use linux (specifically ubuntu of course) as a server. However, all of the "documentation" assumes you even know how to do such simple tasks as save a file which for some reason the default is not to be able to.

Thanks!

---

### Post by heimo on 2005-07-26
I can't comment on how to edit vsftp config, but the saving problem should go away if you do it as a root
 ```
sudo gedit /etc/vsftpd.conf
```

---

### Post by Baci on 2005-07-26
ahh well that much did the trick thanks

---

### Post by Baci on 2005-07-26
everyone keeps saying stuff about vsftd being well documented, and knowing nothing but windows, i havn't a clue where to look for these documents.

I still don't get the logic behind installing a program and having its files go into 50 diffrent folders... but hey welcome to linux i guess.

---

### Post by dataw0lf on 2005-07-27
Add this to your vsftp config file, to allow local users (those contained within said server's /etc/passwd) to login:

local_enable=YES

I don't use any ftp services other than sftp, due to security reasons.  Is there any pressing reasons (e.g., speed) to why you'd use an alternative to sftp?

---

### Post by Baci on 2005-07-27
i was browsing the forums and someone said that this was the best fpt to use, its also the one that i could find on the synaptic package manager

---

### Post by Baci on 2005-07-27
local_enable=YES

still can only connect with anon

---

### Post by Baci on 2005-07-27
here is my config

> [# Example config file /etc/vsftpd.conf
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
ftpd_banner=Welcome to Baci's FTP
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
chroot_local_user=NO
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
# the presence of the "-R" option, so there is a strong case

 for enabling it.
#ls_recurse_enable=YES


#custom
chmod_enable=YES
virtual_use_local_privs=YES
write_enable=YESQUOTE]# Example config file /etc/vsftpd.conf
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
ftpd_banner=Welcome to Baci's FTP
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
chroot_local_user=NO
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
# the presence of the "-R" option, so there is a strong case

 for enabling it.
#ls_recurse_enable=YES


#custom
chmod_enable=YES
virtual_use_local_privs=YES
write_enable=YES[/QUOTE]

---

### Post by Baci on 2005-07-27
for that matter, anyone with aim or msn want to help a newb? 1-2 questions a day with the forums is way to slow for how many questions i have =p

---

### Post by dataw0lf on 2005-07-27
I don't use vsftp, but the config file looks correct.  You've restarted the ftp daemon, yes?

---

### Post by Baci on 2005-07-27
hello slc friend =p I re-started the computer, and I don't know how to start the daemon again let alone restart it ..

---

### Post by dataw0lf on 2005-07-27
I'm unsure what the vsftp daemon is called.  vsftpd?

Try this at the command line:

/etc/init.d/vsftpd start

---

### Post by Baci on 2005-07-27
it said permission denied, so i used sudo, it sayed it was starting it, but whenever i ftp it, it just says the remote computer activley denied connection

---

### Post by Baci on 2005-08-01
still

---

### Post by h4rdwire on 2005-08-02
check  your /etc/hosts.allow and deny files.

I'm new to ubuntu, as much as i can walk through RH better i just couldn't resist ubuntu interface =X

So now i'm just trying to get used to whats the equivelent to certain commands in rh etc etc.

but feel free to IM me maybe we can help each other out baci, p0gib0y

---

