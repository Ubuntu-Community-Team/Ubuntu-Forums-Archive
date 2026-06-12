---
title: "vsftpd worked before 12.04 upgrade"
date: 2012-05-22
forum: Server Platforms
---

### Post by DarwinLabs on 2012-05-22
Hello I am experiencing issues with my VSFTPD installation. it was working fine before I did the 12.04 update which naturally updates all of the packages. My issue is now that when a user tries to connect to my box they can't and after do a packet capture I noticed I am receiving this:

vsftpd: refusing to run with writable root inside chroot

I have gone on the websites and tried making the suggested changes but when they are made nobody can write the the folders anymore.
Below is a copy of my config

```

anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=YES
chroot_local_user=YES
guest_enable=YES
guest_username=ftpuser
listen=YES
listen_port=990
userlist_file=/etc/vsftpd/vsftpd_login.db
userlist_enable=YES
pam_service_name=vsftpd
local_root=/mnt/Storage/FTPROOT/$USER
user_sub_token=$USER
pasv_enable=YES
pasv_min_port=31000
pasv_max_port=32000
file_open_mode=0755
local_umask=000
virtual_use_local_privs=YES
force_dot_files=YES
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
ssl_ciphers=HIGH
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
vsftpd_log_file=/var/log/vsftpd.log

```

Below is an example of my directory structure.

770    /mnt/Storage/FTPROOT
each user has their own directory inside of FTPROOT which is owned by the user mentioned in the config. example user AA and user BB exist like

/mnt/Storage/FTPROOT/AA
/mnt/Storage/FTPROOT/BB

user AA cannot see BB directory and user BB cannot see user AA directory.


any assistance would be appreciated.

Thanks.

---

### Post by maverickaddicted on 2012-05-25
Have you seen this post - 

[http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update](http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update)

Also you can paste the output of your log file (/var/log/vsftpd.log) to get more idea about the error.

---

### Post by gottaa on 2012-05-25
On the link Maverick posted, the first reply is exactly the route I followed to resolve this issue, the other insecure option is changing

```
chroot_local_user=YES
```
to
```
chroot_local_user=NO
```

BUT this on my setup allowed me to go up the folder structure (a bad idea I thought), so I followed the already linked suggestion

---

### Post by maverickaddicted on 2012-05-25
Here is mine vsftpd configuration file - 

```

serveradmin@openserver:~$ cat /etc/vsftpd.conf 
# /etc/vsftpd.conf - vsftpd configuration file
#
# Run standalone
listen=YES
#
# Allow anonymous FTP
anonymous_enable=NO
#
# Allow local users to log in
local_enable=YES
#
# Allow any form of FTP write command
write_enable=YES
#
# Default umask is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd)
local_umask=002
anon_umask=002
#
# Allow the anonymous FTP user to upload files
anon_upload_enable=NO
#
# Allow the anonymous FTP user to be able to create new directories
anon_mkdir_write_enable=NO
#
# Activate directory messages
dirmessage_enable=YES
#
# Display directory listings with the time in your local time zone
use_localtime=YES
#
# Activate logging of uploads/downloads
xferlog_enable=YES
chmod_enable=YES
dirlist_enable=YES
lock_upload_files=NO
virtual_use_local_privs=YES
chown_upload_mode=0777
file_open_mode=0777
# Make sure PORT transfer connections originate from port 20 (ftp-data)
connect_from_port_20=YES
#
# Uploaded anonymous files to be owned by a different user
#chown_uploads=YES
#chown_username=whoever
#
# Log file path
#xferlog_file=/var/log/vsftpd.log
#
# Log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# Customise the login banner string
ftpd_banner=Welcome to OpenServer
#
# Use the contents of this file for the login banner
#banner_file=/etc/vsftpd/banner
#
# Restrict local users to their home directories
chroot_local_user=YES
#
# List of local users to chroot() to their home directory. If
# chroot_local_user is YES, then this list becomes a list of users to NOT
# chroot()
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd/chroot_list
#
# Activate the "-R" option to the builtin ls. This is disabled by default to
# avoid remote users being able to cause excessive I/O on large sites.
# However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option
ls_recurse_enable=YES
#
# Show textual names in the user and group fields of directory listings
text_userdb_names=YES
#
# Empty directory not writable by the ftp user as a secure chroot() jail at
# times vsftpd does not require filesystem access
secure_chroot_dir=/var/run/vsftpd/empty
#
# PAM service vsftpd will use
pam_service_name=vsftpd
serveradmin@openserver:~$ 

```

---

### Post by icaka92 on 2012-05-29
Hello. I have the same problem. My vsftpd worked fine before last update to 12.04.  I need to use vsftp to edit files of my site (var/www/). I try to reinstall my vsftpd but no effect. What command should i follow to install correct vsftpd and to edit my files in var/www. I only want to connect to my computer and to have access to my site files and to edit it. With ubuntu 11.XX i don't have problems, but now ... On my ubuntu 11.XX i access to my files with FileZilla Client and write for password my ubuntu password. Can somebody explain me how to make this on my new ubuntu. 

Thanks !

---

### Post by maverickaddicted on 2012-05-30
> **icaka92 said:**
> Hello. I have the same problem. My vsftpd worked fine before last update to 12.04.  I need to use vsftp to edit files of my site (var/www/). I try to reinstall my vsftpd but no effect. What command should i follow to install correct vsftpd and to edit my files in var/www. I only want to connect to my computer and to have access to my site files and to edit it. With ubuntu 11.XX i don't have problems, but now ... On my ubuntu 11.XX i access to my files with FileZilla Client and write for password my ubuntu password. Can somebody explain me how to make this on my new ubuntu. 

Thanks !

Have you tried this -

[http://askubuntu.com/questions/12818...g-after-update]("http://askubuntu.com/questions/128180/vsftpd-stopped-working-after-update")

If it is not working then please paste the output of your log file it will help others also to get more clear idea.

---

### Post by icaka92 on 2012-06-05
I have tried this :

```
i chmod the folder that my ftp user comes in to as he first login (root  folder) by using in terminal: "sudo chmod a-w /home/user"
```

But no effect. And i must try to create a new folder in the maind folder, but now i only have access on ubuntu via putty and can't use text editor.

---

### Post by maverickaddicted on 2012-06-06
> **icaka92 said:**
> I have tried this :

```
i chmod the folder that my ftp user comes in to as he first login (root  folder) by using in terminal: "sudo chmod a-w /home/user"
```

But no effect. And i must try to create a new folder in the maind folder, but now i only have access on ubuntu via putty and can't use text editor.

Why you need text editor to create a folder. You can create it using this command - 

```
mkdir foldername
```

Also if you want to create file insdie that folder, you can use this command---

```
nano filename.txt
```

---

### Post by icaka92 on 2012-06-06
No no. I don't have installed vsftpd on my ubuntu and i think I need text editor to config them via putty or can you tell me the command that i must follow to install vsftp and to have access only on that folder: /var/www and subfolder  and to access it with my ubuntu username and password.

---

### Post by maverickaddicted on 2012-06-07
> **icaka92 said:**
> No no. I don't have installed vsftpd on my ubuntu and i think I need text editor to config them via putty or can you tell me the command that i must follow to install vsftp and to have access only on that folder: /var/www and subfolder  and to access it with my ubuntu username and password.

Ok, so you have not installed vsftpd on your server. Is this correct?

---

### Post by icaka92 on 2012-06-07
I have been installed it before, but i remove it, because i don't have access to them. What command should follow now to install it correct and to access /var/www folder with my ubuntu user and password?

---

### Post by maverickaddicted on 2012-06-08
> **icaka92 said:**
> I have been installed it before, but i remove it, because i don't have access to them. What command should follow now to install it correct and to access /var/www folder with my ubuntu user and password?

You have to install it in the same way as you install it before -

```
sudo apt-get install vsftpd
```

Then you have to edit /etc/vsftpd.conf, Here is mine - 

```

serveradmin@openserver:~$ cat /etc/vsftpd.conf
# /etc/vsftpd.conf - vsftpd configuration file
#
# Run standalone
listen=YES
#
# Allow anonymous FTP
anonymous_enable=NO
#
# Allow local users to log in
**local_enable=YES**
#
# Allow any form of FTP write command
**write_enable=YES**
#
# Default umask is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd)
[B]local_umask=002
anon_umask=002[/B]
#
# Allow the anonymous FTP user to upload files
anon_upload_enable=NO
#
# Allow the anonymous FTP user to be able to create new directories
anon_mkdir_write_enable=NO
#
# Activate directory messages
dirmessage_enable=YES
#
# Display directory listings with the time in your local time zone
use_localtime=YES
#
# Activate logging of uploads/downloads
[B]xferlog_enable=YES
chmod_enable=YES
dirlist_enable=YES
lock_upload_files=NO
virtual_use_local_privs=YES
chown_upload_mode=0777  # it is local development server only, that's why I have
file_open_mode=0777[/B]     # set it to 777, you can change accordingly 
# Make sure PORT transfer connections originate from port 20 (ftp-data)
connect_from_port_20=YES
#
# Uploaded anonymous files to be owned by a different user
#chown_uploads=YES
#chown_username=whoever
#
# Log file path
#xferlog_file=/var/log/vsftpd.log
#
# Log file in standard ftpd xferlog format
#xferlog_std_format=YES
#
# Customise the login banner string
ftpd_banner=Welcome to OpenServer
#
# Use the contents of this file for the login banner
#banner_file=/etc/vsftpd/banner
#
# Restrict local users to their home directories
**chroot_local_user=YES**
#
# List of local users to chroot() to their home directory. If
# chroot_local_user is YES, then this list becomes a list of users to NOT
# chroot()
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd/chroot_list
#
# Activate the "-R" option to the builtin ls. This is disabled by default to
# avoid remote users being able to cause excessive I/O on large sites.
# However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option
ls_recurse_enable=YES
#
# Show textual names in the user and group fields of directory listings
text_userdb_names=YES
#
# Empty directory not writable by the ftp user as a secure chroot() jail at
# times vsftpd does not require filesystem access
secure_chroot_dir=/var/run/vsftpd/empty
#
# PAM service vsftpd will use
pam_service_name=vsftpd
serveradmin@openserver:~$

```

I have made the changes in bold, which I have made, since mine is only for internal purpose;it is not connected to external world, there is not much thought about security.
After, making the necessary changes, restart vsftpd service

```
sudo service vsftpd restart
```

Then you have to create user.

```
sudo useradd -d /var/www/ -g groupname -s /bin/false username
```
```
sudo passwd username
```

You have to also change the permission of folder.

---

### Post by icaka92 on 2012-06-11
Hello. Thank you for exhaustive response. I understand all, without this commands:

```
# Default umask is 077. You may wish to change this to 022, # if your users expect that (022 is used by most other ftpd) 
local_umask=002 
anon_umask=002

# Activate logging of uploads/downloads 
xferlog_enable=YES 
chmod_enable=YES 
dirlist_enable=YES 
lock_upload_files=NO 
virtual_use_local_privs=YES 
chown_upload_mode=0777  # it is local development server only, that's why I have file_open_mode=0777     # set it to 777, you can change accordingly
```
Could you explain me what must be my settings to use vsftp to control files on /var/www .

---

### Post by maverickaddicted on 2012-06-12
> **icaka92 said:**
> Hello. Thank you for exhaustive response. I understand all, without this commands:

```
# Default umask is 077. You may wish to change this to 022, # if your users expect that (022 is used by most other ftpd) 
local_umask=002 
anon_umask=002

# Activate logging of uploads/downloads 
xferlog_enable=YES 
chmod_enable=YES 
dirlist_enable=YES 
lock_upload_files=NO 
virtual_use_local_privs=YES 
chown_upload_mode=0777  # it is local development server only, that's why I have file_open_mode=0777     # set it to 777, you can change accordingly
```Could you explain me what must be my settings to use vsftp to control files on /var/www .

local_umask=002  - > default permission for creating files which would be 775 (777-002).
anon_umask=002 -> umask value for anonymous users.

xferlog_enable=YES -> maintaining details of uploading and downloading in log file
chmod_enable=YES  - Allow the SITE CHMOD command in ftp client software for changing file permissions
dirlist_enable=YES -> to enable directory listing command in ftp client software
lock_upload_files=NO -> remove the write lock from uploaded file.
virtual_use_local_privs=YES -> if you are using virtual users, then it will give that virtual user same privileges as local user.

# These two came out of the frustration of file permission problems that I have faced.

chown_upload_mode=0777  
file_open_mode=0777 

However, you will learn more from here, please read it to understand every configuration settings in vsftpd.conf file -

[https://security.appspot.com/vsftpd/vsftpd_conf.html](https://security.appspot.com/vsftpd/vsftpd_conf.html)

---

### Post by icaka92 on 2012-06-17
Hello. I update my vsftpd.conf like your, but now i am getting this error:

**Connection attempt failed with "ECONNREFUSED - Connection refused by server**

What should i do to correct that. I follow steps that you write, but no effect.

---

### Post by maverickaddicted on 2012-06-18
> **icaka92 said:**
> Hello. I update my vsftpd.conf like your, but now i am getting this error:

**Connection attempt failed with "ECONNREFUSED - Connection refused by server**

What should i do to correct that. I follow steps that you write, but no effect.

Can you check vsftpd service is running or not OR port 21 is not being blocked by the firewall?

---

### Post by icaka92 on 2012-06-19
I am newbie with ubuntu. Can you help me with command to check it. Thank you !

---

### Post by maverickaddicted on 2012-06-20
> **icaka92 said:**
> I am newbie with ubuntu. Can you help me with command to check it. Thank you !

Ok, there is already one thread for checking, just go through it and if you face any problem post it here.

[http://ubuntuforums.org/showthread.php?t=1716466](http://ubuntuforums.org/showthread.php?t=1716466)

If port 21 is blocked by firewall, you can open it via this command -

```
sudo iptables -A INPUT -p tcp -m tcp --dport 21 -j ACCEPT 
```

---

### Post by icaka92 on 2012-06-21
Hello. Thank you for the post. I understand that my vsftp server stop/waiting. I try to start it with this command:
```

sudo /etc/init.d/vsftpd start
```And receive that message:

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd
vsftpd start/pre-start, process 24205

My firewall is inactive. I check it with this commnad: 
sudo ufw status

Where can be the problem?

---

### Post by maverickaddicted on 2012-06-22
> **icaka92 said:**
> Hello. Thank you for the post. I understand that my vsftp server stop/waiting. I try to start it with this command:
```

sudo /etc/init.d/vsftpd start
```And receive that message:

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start vsftpd
vsftpd start/pre-start, process 24205

My firewall is inactive. I check it with this commnad: 
sudo ufw status

Where can be the problem?

you have to use this command to start the vsftp service.

```
sudo service vsftpd start
```

---

### Post by icaka92 on 2012-06-22
I have really strange problem. When i run this:

```
sudo service vsftpd start
```i receive this message: ```
vsftpd start/running, process 7752
```and after that when i run this: ```
service vsftpd status
```i get this message: ```
vsftpd stop/waiting
```

---

### Post by maverickaddicted on 2012-06-25
Check the log file, if you can find something in it -

```
sudo tail -f /var/log/vsftpd.log
```
```
sudo tail -f /var/log/messages
```
```
sudo tail -f /var/log/syslog
```

Can you paste your configuration file (/etc/vsftpd.conf)?

---

### Post by icaka92 on 2012-06-28
Hello,

When I run this command in termnal: 
```
sudo tail -f /var/log/vsftpd.log
``` I don't receive anything.

When I run this command:

```
sudo tail -f /var/log/messages
```tail: cannot open `/var/log/messages' for reading: No such file or directory


And when I run this commnad:

```
sudo tail -f /var/log/syslog
```I receive this

```
Jun 28 20:39:01 ico-desktop CRON[30175]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jun 28 20:39:02 ico-desktop CRON[30174]: (CRON) info (No MTA installed, discarding output)
Jun 28 21:09:01 ico-desktop CRON[30764]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jun 28 21:09:02 ico-desktop CRON[30763]: (CRON) info (No MTA installed, discarding output)
Jun 28 21:17:01 ico-desktop CRON[30904]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 28 21:39:01 ico-desktop CRON[31406]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jun 28 21:39:01 ico-desktop CRON[31405]: (CRON) info (No MTA installed, discarding output)
Jun 28 22:09:01 ico-desktop CRON[31996]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Jun 28 22:09:01 ico-desktop CRON[31995]: (CRON) info (No MTA installed, discarding output)
Jun 28 22:17:01 ico-desktop CRON[32191]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```This is my vsftpd.conf file

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
allow_writable_root=YES
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
local_umask=002
anon_umask=002
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
chmod_enable=YES
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
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_list_enable=NO
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
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```I really hope so to can config it correct, because i need to have remote control on my files.

---

### Post by maverickaddicted on 2012-06-29
Ok, connect to your server using ssh -

1) ```
netstat -an | grep "LISTEN"
```

   Check whether port 21 is in listening state or not

OR

1) you can install nmap, which is very useful utility for checking the openport - 

```
sudo apt-get install nmap
```
```
nmap hostname
```

Since you are running this command on server itself, use "localhost" as hostname.

2)If port 21 is not listed then open it using this command -

```
sudo iptables -A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
```

3)```
sudo service vsftpd stop
```
  ```
sudo service vsftpd start
```

---

### Post by icaka92 on 2012-06-29
I follow the steps that you write, but I am thinking that can't listen port 21.

When I run this command
```
netstat -an | grep "LISTEN"
```I receive that

```
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     7628     /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     2285537  /tmp/keyring-CXDqzu/control
unix  2      [ ACC ]     STREAM     LISTENING     2282416  /tmp/ssh-NkVZGvN12011/agent.12011
unix  2      [ ACC ]     STREAM     LISTENING     2287805  /tmp/.ICE-unix/12011
unix  2      [ ACC ]     STREAM     LISTENING     2290719  /tmp/keyring-CXDqzu/gpg
unix  2      [ ACC ]     STREAM     LISTENING     2290063  /tmp/keyring-CXDqzu/pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     2290064  /tmp/keyring-CXDqzu/ssh
unix  2      [ ACC ]     STREAM     LISTENING     4480807  /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     2290304  /home/ico/.pulse/de417a64a9f831ed0543bb2400000006-runtime/native
unix  2      [ ACC ]     STREAM     LISTENING     11315    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     3034     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     2287804  @/tmp/.ICE-unix/12011
unix  2      [ ACC ]     STREAM     LISTENING     9546     @/org/bluez/audio
unix  2      [ ACC ]     SEQPACKET  LISTENING     7004     /run/udev/control
unix  2      [ ACC ]     STREAM     LISTENING     7627     @/tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     10360    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     1481     /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     8668     /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     2290029  @/tmp/dbus-pugmEPgQoN
unix  2      [ ACC ]     STREAM     LISTENING     2289178  @/tmp/dbus-gw4wpdmSdu
unix  2      [ ACC ]     STREAM     LISTENING     10489    /var/run/mysqld/mysqld.sock
```I install nmap and when I run 
```
nmap localhost
```I receive this 

```
Starting Nmap 5.21 ( http://nmap.org ) at 2012-06-29 15:11 EEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00030s latency).
Not shown: 994 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
53/tcp    open  domain
80/tcp    open  http
631/tcp   open  ipp
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.09 seconds

```I try to listed port 21 with this command

```
sudo iptables -A INPUT -p tcp -m tcp --dport 21 -j ACCEPT
```And after that i check it with

```
nmap hostname
```And i receive this

```
Starting Nmap 5.21 ( http://nmap.org ) at 2012-06-29 15:13 EEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00031s latency).
Not shown: 994 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
53/tcp    open  domain
80/tcp    open  http
631/tcp   open  ipp
3306/tcp  open  mysql
10000/tcp open  snet-sensor-mgmt

Nmap done: 1 IP address (1 host up) scanned in 0.07 seconds

```The same like other time.

After that i run

```
sudo service vsftpd stop
```And receive
```

stop: Unknown instance: 
```After that i run last command

```
sudo service vsftpd start
```And receive

```
vsftpd start/pre-start, process 15597
```After all i check if vsftpd work with

```
sudo service vsftpd start
```And receive

```
vsftpd stop/waiting
```I don't know where is the problem. Thank you for help!

---

### Post by icaka92 on 2012-07-07
Any ideas ?

---

### Post by amilauduwerella on 2013-03-13
If you want to have chroot_list_enable=YES

then;
uncomment following;

chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list

and put all users in to "/etc/vsftpd.chroot_list" file

and then restart vsftpd

---

### Post by ranger12 on 2013-03-13
What version of vsftpd are you using? I have 2.3.5 and am using Srever 12.04.2. I experimented with the allow_writtable_root=yes and it would not allow me to connect. If you look at vsftpd's website in the changelog for 2.3.5 he does state he added that option but it does not seem to work or at least on my server it doesn't. If this is your version than trying remming that and see what happens. It's not a big deal for me since I just organize everything into nested folders under /srv/ftp but this may not be to your liking.

---

### Post by rafaelbordignon on 2013-05-14
Hi all,
 I faced the same problem using Ubuntu 12.10 and the default vsftpd package, but during my debugging process I found this .deb already patched for Ubuntu 12.10.

 [http://blog.desertbushtech.com/2013/02/i-use-ubuntu.html](http://blog.desertbushtech.com/2013/02/i-use-ubuntu.html)

 I hope this also helps other 12.10 users :).

---

