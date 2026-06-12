---
title: "vsFTPd Permissions Wrangling"
date: 2011-12-13
forum: Server Platforms
---

### Post by KalebZen on 2011-12-13
This issue has been resolved. WinSCP, the client I was using to upload, was setting chmod during transfers. You can either disable this on the client or add chmod_enable=NO to /etc/vsftpd.conf.

Not another vsftpd permissions question huh?


----------

I am running Ubuntu 11.10 as a development LAMP server. I have tried to setup vsftpd, but can't seem to get the correct permissions applied to files I upload.

I have scoured the net for quite some time and came up with the file_open and local_umask settings, but they both seem to be ignored when I upload a simple text file.

Here is my /etc/vsftpd.conf file:

```
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
connect_from_port_20=YES
xferlog_enable=YES
xferlog_file=/var/log/vsftpd/vsftpd.log
nopriv_user=nobody
chroot_list_enable=NO
chroot_local_user=NO
background=YES
listen=YES
file_open_mode=0775
local_umask=002
```

If there is anymore info needed to help me out please let me know and I would be happy to post it. I have setgid to www-data for /var/www and put myself in that group as well.

Thx, I am fairly new to ubuntu and would really appreciate the help.

---

### Post by integrilogic on 2012-03-01
I am also new to linux (Ubuntu). I have installed vsfptd, and edited the /etc/vsftpd.conf file with the following settings:

listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to UNEEDIT-Web
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem

I have created a folder here /var/opt/godatafeed, these are the permissions on the directory:

drwxrwxrwx 3 root godatafeed 4096 Feb 28 23:04 godatafeed

Inside this folder is a symbolic link to /var/opt/fb, I created with this command:

ln -s /var/opt/fb/ /var/opt/godatafeed/

In the folder /var/opt/fb, the permissions are:

drwxr--r-- 2 root godatafeed 4096 Feb 28 22:46 fb

In the folder where the symbolic link is created /var/opt/godatafeed/fb, these are the permissions:

lrwxrwxrwx 1 root root 12 Feb 28 23:04 fb -> /var/opt/fb/

The issue I am having is, is that I need only read access for the group "godatafeed" to the symbolic link, currently it is only set for root access. But I did notice that the last permissions group "o (other/everyone)" is set for rwx, but I can get access to the fb folder when ftp'ing in. I have the home directory set as:

useradd godatafeed -d /var/opt/godatafeed/ -s /bin/false

I can successfully log in with the username for ftp and browse the home directory, but I can't get to the "fb" directory.

How do I set the permissions correctly so only the root of the folder /var/opt/godatafeed just has read only permissions, as well as getting access to the "fb" symbolic link inside of the "godatafeed" folder? 

Thank you

---

