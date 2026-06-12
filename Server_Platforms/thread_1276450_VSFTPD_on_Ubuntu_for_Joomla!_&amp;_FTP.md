---
title: "VSFTPD on Ubuntu for Joomla! &amp; FTP"
date: 2009-09-27
forum: Server Platforms
---

### Post by Stoneface on 2009-09-27
I am installing Joomla! on my local Ubuntu server. To make Joomla! run smoothly I need FTP access. I decided to install VSFTP
```
 sudo apt-get install vsftpd 
```
started the service:
```
 sudo /etc/init.d/vsftpd start 
```
Then I realized I needed to added myself to FTP users. I found info here: [http://linux-hacks.blogspot.com/2008/09/adding-new-users-to-vsftpd.html](http://linux-hacks.blogspot.com/2008/09/adding-new-users-to-vsftpd.html) and created vsftpd.chroot_list in /etc/ using
```
sudo gedit vsftpd.chroot_list
```
I added my user name and restarted the VSFTP service:
```
sudo /etc/init.d/vsftpd restart
```
Then I resumed the J! setup. I entered the FTP details and clicked autofind path. I got the error: "Could not connect to FTP Server"
Any ideas why? Password and user should be correct...

---

### Post by Stoneface on 2009-09-27
made a few changes in vsftpd.conf:
```

# Uncomment this to allow local users to log in.
local_enable=YES

```
and
```

# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
#chroot_list_enable below.
chroot_local_user=YES

```

Restarted the vsftpd service.```
sudo /etc/init.d/vsftpd restart

```

Had a new error: Not able to auto-detect the FTP root folder

---

### Post by Stoneface on 2009-09-27
I made another change:
```

# Sets root directory for non-anonymous users
local_root=/var/www/cms

```

Restarted the service and tried again. Still getting: "Not able to auto-detect the FTP root folder"

Just read:
[I]This option represents a directory which vsftpd will try to change into after a local (i.e. non-anonymous) login. Failure is
silently ignored.[/I]
So I guess my chroot is somehow not working??

Here is my vsftpd.conf using ```
grep -v '^#' /etc/vsftpd.conf
```:
```
listen=YES
anonymous_enable=NO
local_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to Jubuntu FTP
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=/var/www/cms

```

---

### Post by Stoneface on 2009-09-27
New vsftpd.conf

```
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_std_format=YES
ftpd_banner=Welcome to Jubuntu FTP
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

When I use this configuration:
```

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_std_format=YES
ftpd_banner=Welcome to Jubuntu FTP
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key


```

No change either... 
Still no FTP root path found!!!! Anybody????

---

### Post by Stoneface on 2009-09-27
The funny thing is that I can FTP to my local server now
```

me@my-laptop:/etc$ ftp localhost
Connected to localhost.
220 Welcome to Jubuntu FTP
Name (localhost:me): me
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
```

So why can't joomla! find the ftp root path???

---

### Post by Stoneface on 2009-09-27
Maybe it has something to do with user permissions on my box?
The joomla! folder is now in the group www-data and so is the user (me) I use to access the server by ftp. I can FTP to the localhost without any problems and wind up in the root folder I have set in the vsftpd.conf... So what is the problem here?

---

### Post by Stoneface on 2009-09-27
Well I used / as path to ftp root. Finished the installation and removed the installation file. Now when I want to upload and unpack a component I have to enter FTP data. And then I still have issues: ```
JFTP::store: Bad response Warning! Failed to move file.
```
This is starting to bug me... So I checked the file permissions on my joomla folder and saw this:
```
drwxr-xr-x 16 www-data   33     4096 2009-09-27 15:42 joomla
```
well I```
sudo chown -R me /var/www/joomla
```
and got this doing ls -l ```
drwxr-xr-x 16 me   33     4096 2009-09-27 15:42 joomla
```
Now I still need to replace 33 by an actual existing group..
Did that ```
sudo chgrp -R me joomla
```
Then I added the ftp details to configuration.php and all was cool. I guess it was a basic file and group permission issue in the end.

---

