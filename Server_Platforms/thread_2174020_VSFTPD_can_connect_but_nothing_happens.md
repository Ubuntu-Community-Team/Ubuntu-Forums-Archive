---
title: "VSFTPD can connect but nothing happens"
date: 2013-09-12
forum: Server Platforms
---

### Post by niwreg on 2013-09-12
Hi,

I have a ubuntu server with is running Ubuntu 13.04. I had vsftpd installed with apt-get install vsftpd.

I then tried to make virtual users to work but it didn't so i deleted everything that i created or was created dit apt-get purge vsftpd and so on.

Then i tried to install vsftpd again but i wanted it to work with local users. 

the problem is that no matter what i tried in the config, vsftpd will start and say it's running, and it actualy is because i can connect with ftp localhost to te server. but all i get is this:

:~$ ftp 127.0.0.1
Connected to 127.0.0.1.


and then there goes nothing. I can't find any log files that are created. 

My config is this:

```
 cat /etc/vsftpd.conf
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
#write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
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
ftpd_banner=Welcome to blah FTP service.
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
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key



```


Did i do something wrong with the config?

---

### Post by aschlosberg on 2013-09-18
In one terminal run:

```

tail -f /var/log/vsftpd.log;

```

and in another attempt to log in. Please copy and paste the output from the log file here and we can help you further.

---

### Post by niwreg on 2013-09-19
The log only contains this:

gerwin@nagios:~$ tail -f /var/log/vsftpd.log;
Mon Sep 16 12:24:58 2013 [pid 25510] CONNECT: Client "80.79.39.113"


That was when i tried to connect with the ftp client with telnet to see the raw data that maybe is sent back. I don't get this working anymore so i guess it was a lucky call or something

When I run:

```
gerwin@nagios:~$ ps -ef | grep vsftpd
nobody     655     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody     888     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody     942     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody     961     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody    1006     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody    1028     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody    1110     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody    1117     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody    3760     1  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody    3889     1  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody    3892     1  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
root      4565     1  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
root      4568  4565  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody    4569  4568  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
root      4576  4565  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody    4577  4576  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody   16646     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
root     19126  4565  0 Sep17 ?        00:00:00 /usr/sbin/vsftpd
nobody   19127 19126  0 Sep17 ?        00:00:00 /usr/sbin/vsftpd
nobody   21735     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   23777     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
root     24281  4565  0 07:59 ?        00:00:00 /usr/sbin/vsftpd
nobody   24282 24281  0 07:59 ?        00:00:00 /usr/sbin/vsftpd
root     24296  4565  0 08:00 ?        00:00:00 /usr/sbin/vsftpd
nobody   24297 24296  0 08:00 ?        00:00:00 /usr/sbin/vsftpd
root     24379  4565  0 08:01 ?        00:00:00 /usr/sbin/vsftpd
nobody   24380 24379  0 08:01 ?        00:00:00 /usr/sbin/vsftpd
root     24492     1  0 Sep10 ?        00:00:00 /usr/sbin/vsftpd
nobody   24493 24492  0 Sep10 ?        00:00:00 /usr/sbin/vsftpd
root     24682  4565  0 08:03 ?        00:00:00 /usr/sbin/vsftpd
nobody   24683 24682  0 08:03 ?        00:00:00 /usr/sbin/vsftpd
gerwin   24979 23947  0 08:10 pts/0    00:00:00 grep --color=auto vsftpd
nobody   25470     1  0 Sep10 ?        00:00:00 /usr/sbin/vsftpd
nobody   25481     1  0 Sep10 ?        00:00:00 /usr/sbin/vsftpd
root     25509     1  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody   25510 25509  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody   25596     1  0 Sep16 ?        00:00:00 /usr/sbin/vsftpd
nobody   25631     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   25845     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
root     29007     1  0 Sep09 ?        00:00:00 /usr/sbin/vsftpd
nobody   29008 29007  0 Sep09 ?        00:00:00 /usr/sbin/vsftpd
nobody   29025     1  0 Sep09 ?        00:00:00 /usr/sbin/vsftpd
nobody   29431     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   29475     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   29482     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   29575     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   30726     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   32182     1  0 Sep12 ?        00:00:00 vsftpd /etc/vsftpd.conf
nobody   32209     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   32307     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd
nobody   32362     1  0 Sep12 ?        00:00:00 /usr/sbin/vsftpd



```

---

### Post by niwreg on 2013-09-26
Little update,

After an reboot i can connect however i cannot login

this is the output of my ftp session:

rtv8@vps:~$ ftp ftp.xxx.xxx
Connected to ftp.xxx.xxx.
220 (vsFTPd 3.0.2)
Name (dronten.rtv8.nl:rtv8): <user>
331 Please specify the password.
Password:


and then it hangs. 

output of the log:

Thu Sep 26 10:51:07 2013 [pid 28133] CONNECT: Client "91.213.195.7"


After forced closing ftp session  i cannot connect anymore all i get is the connected thing again. 


There seems to be vsftpd processes beeing created but not ended or something. Because for every attemp i get 2 more processes. 

```

gerwin@nagios:~$ ps aux | grep vsftpd
root      1161  0.0  0.0   4872    72 ?        Ss   Sep23   0:00 /usr/sbin/vsftpd
root     28132  0.0  0.1   6800  1528 ?        Ss   10:51   0:00 /usr/sbin/vsftpd
nobody   28133  0.0  0.0   5020   676 ?        S    10:51   0:00 /usr/sbin/vsftpd
gerwin   28154  0.0  0.1  17556  1008 ?        S    10:51   0:00 /usr/sbin/vsftpd
root     28169  0.0  0.0   4872   616 ?        Ss   10:51   0:00 /usr/sbin/vsftpd
nobody   28170  0.0  0.0   5008   676 ?        S    10:51   0:00 /usr/sbin/vsftpd
gerwin   28454  0.0  0.0   3952   812 pts/0    S+   10:52   0:00 grep --color=auto vsftpd
gerwin@nagios:~$ ps aux | grep vsftpd


root      1161  0.0  0.0   4872    72 ?        Ss   Sep23   0:00 /usr/sbin/vsftpd
root     28132  0.0  0.1   6800  1528 ?        Ss   10:51   0:00 /usr/sbin/vsftpd
nobody   28133  0.0  0.0   5020   676 ?        S    10:51   0:00 /usr/sbin/vsftpd
gerwin   28154  0.0  0.1  17556  1008 ?        S    10:51   0:00 /usr/sbin/vsftpd
root     28169  0.0  0.0   4872   616 ?        Ss   10:51   0:00 /usr/sbin/vsftpd
nobody   28170  0.0  0.0   5008   676 ?        S    10:51   0:00 /usr/sbin/vsftpd
root     28455  0.0  0.0   4872   616 ?        Ss   10:52   0:00 /usr/sbin/vsftpd
nobody   28456  0.0  0.0   5008   676 ?        S    10:52   0:00 /usr/sbin/vsftpd
gerwin   28458  0.0  0.0   3952   812 pts/0    S+   10:52   0:00 grep --color=auto vsftpd

```

---

