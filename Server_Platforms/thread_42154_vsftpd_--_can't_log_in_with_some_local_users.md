---
title: "vsftpd -- can't log in with some local users"
date: 2005-06-16
forum: Server Platforms
---

### Post by Grey on 2005-06-16
Hi everyone.  First of all, I should mention that I am running Debian Sarge 3.1 on my server.  But I really hope someone can help me anyway.  I just don't know where else to go, and I've gotten some great help on these forums before.  What I suspect is going on is a problem with PAM.  But I have no idea what PAM is, or how to fix it.

Basically, I have one non-root user I created when I first installed Debian.  That user works just fine.  I can FTP in, I can access Samba shares, I can SSH in, it's beautiful.  But any user that I've created since then, is unable to actually log into the FTP server.  With other users, I can SSH in, I can access Samba shares, and I can do all sorts of stuff.  But I can't for the life of me figure out why only one user has FTP access.

I've checked /etc/ftpusers, and I've tried just about every configuration of vsftpd.conf that I could think of.  This is how I have it set up at the moment.  Any help would be greatly appreciated.

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
local_umask=775
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
ftpd_banner=Welcome to Yoda.
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
rsa_cert_file=/etc/ssl/certs/vsftpd.pem

userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
userlist_deny=NO
check_shell=NO

```

---

### Post by defkewl on 2005-06-16
Which one user is able to log in? You said that you only created one non root user. I still don't understand your problem :)

---

### Post by LordHunter317 on 2005-06-16
Did you update /etc/vsftpd.user_list as necessary, you know, like the 3rd last configuration file directive notes?

---

### Post by Grey on 2005-06-16
I have 3 non-root users.  "admin" was created at install time.  "grey" was created later, as was "wwwuser".  admin is the only one capable of logging into the ftpserver.

And yes, I edited the /etc/vsftpd.user_list file to include grey, wwwuser, and admin.  It didn't really seem to do much, and when I removed the names in the file, it didn't even get to the password part.  It just said permission denied when I put in my user name.

As it stands, I get a 530: Login Failed error from the server.

---

### Post by LordHunter317 on 2005-06-16
Did you assign these users passwords via passwd?

Can you login into their accounts interactively?

---

### Post by Grey on 2005-06-16
The server is currently in another room, has no monitor or keyboard, and I SSH in to do all my work... perhaps this might be the root of the problem?  I can SSH into the accounts just fine, as well as access their home directories via samba.  And yes, I assigned passwords via passwd.  It's just the FTP that's not working.

I should also probably mention that I have tried proftpd on the server as well, but I switched to vsftpd in the hopes that it would solve the problem.  It did not. (obviously).

---

### Post by LordHunter317 on 2005-06-16
Look at /usr/share/doc/vsftpd/README.Debian, it's likely to be more helpful than I am.  If it doesn't cover it, post /etc/pam.d/vsftpd.

---

### Post by Grey on 2005-06-16
Thanks.  I will do that when I get home, I am at work right now.  But thanks a whole lot for your assistance so far.

---

### Post by Grey on 2005-06-17
```
# Standard behaviour for ftpd(8).
auth    required        pam_listfile.so item=user sense=deny file=/etc/ftpusers onerr=succeed

# Note: vsftpd handles anonymous logins on its own.  Do not enable
# pam_ftp.so.

# Standard blurb.
@include common-account
@include common-session

@include common-auth
auth    required        pam_shells.so

```

That's my /etc/pam.d/vsftpd file...  I still have no real solution for this.  :(

---

### Post by relix42 on 2005-06-17
Are the users prompted for a password or are they denied access before that password is requested?

---

### Post by Grey on 2005-06-17
they are denied when entering the password.  I enter the valid password, and it coughs up a 530 error.

---

### Post by abood on 2005-06-17
hi there,
guys i activated my ftp server early, and when i log with my account it login and with a password and i can surf all my box with it  and i also added another account sucssesfuly but im wondering on how can i restrict that  the new accout cant go to another folders except that one that i put it in it. for example "/home/ftp/Movies" i need him to be just in that folder ??
thx 
Abood

---

### Post by abood on 2005-06-17
[QUOTE=abood]hi there,
guys i activated my ftp server early, and when i log with my account it login and with a password and i can surf all my box with it  and i also added another account sucssesfuly but im wondering on how can i restrict that  the new accout cant go to another folders except that one that i put it in it. for example "/home/ftp/Movies" i need him to be just in that folder ??
thx 
Abood[/QUOTE]
[B]thx all, sorry for bothiring but i find the solution.

and for the upper posts (grey proplem) maybe ur proplem in the account setting try to change the shell type from /bin/false to /bin/bash and i think it will login correctly without proplems :).[/B]

---

### Post by Grey on 2005-06-18
[QUOTE=abood][B]thx all, sorry for bothiring but i find the solution.

and for the upper posts (grey proplem) maybe ur proplem in the account setting try to change the shell type from /bin/false to /bin/bash and i think it will login correctly without proplems :).[/B][/QUOTE]


Dude....  THANK YOU.

---

### Post by whistl on 2005-06-18
FTP daemons typically require the login shell of accounts be listed in  /etc/shells.  If the accounts that couldn't login were setup with non-standard shells, such as "/bin/false", then add "/bin/false" to /etc/shells, and they should be able to ftp.

---

### Post by LordHunter317 on 2005-06-18
That's odd, as vsftpd is set to not care about the shell, perhaps it's something in the PAM stack.

Unless you had the shell set to /bin/false, which isn't a valid shell ever.  If you need to give a valid shell but not let anyone login, use /bin/true.

---

### Post by Grey on 2005-06-19
[QUOTE=LordHunter317]That's odd, as vsftpd is set to not care about the shell, perhaps it's something in the PAM stack.

Unless you had the shell set to /bin/false, which isn't a valid shell ever.  If you need to give a valid shell but not let anyone login, use /bin/true.[/QUOTE]

Yeah, that was my thought in the matter as well.  I was lazy, and didn't check which shell my new accounts were using thoroughly.  But I added the line to vsftpd to remove shell checking, and it didn't solve anything.  So I had just assumed that it wasn't an issue.

But actually changing the user's shell to bash did indeed fix the problem.  So who knows.

---

### Post by LordHunter317 on 2005-06-19
Well, to test, make sure /bin/true is not in /etc/shells and set an FTP user's shell (one that doesn't need SSH) to /bin/true.  

I'm mostly certain that it is due to the fact /bin/false always fails (returns 1) when run.  Which causes PAM to abort, even if vsftpd doesn't care.

---

### Post by lukanova on 2008-03-04
hi

just wanted to say that i had problems with many users who were in users_list being denied access as ' login incorrect, login failed, ' only because they had /bin/false as their shell specified in /etc/passwd. adding /bin/false to /etc/shells solved the issue.

if /bin/true is not in /etc/shells and /bin/true is specified in /etc/passwd as a shell for particular user, vsftpd will still say login incorrect, login failed' again. so the shell specified in passwd MUST be also specified in /etc/shells. so it seems at least by trial and error.

hope somebody helps. i found the above mention of /etc/shells very helpful as it solved my problem.

good day and catch some sun.

---

