---
title: "VSFTPD - limit directory and uploading files"
date: 2011-11-18
forum: Server Platforms
---

### Post by jodlajodla on 2011-11-18
Hello!

I'm newbie with working with Ubuntu Server, so I have a few questions about VSFTPD.

1. How to limit directory where can users uploading their files?
2. How to set /var/www permissions for uploading files from FTP?

Thanks in advance! :)

---

### Post by integrilogic on 2012-02-28
I am also new to linux (Ubuntu).  I have installed vsfptd, and edited the /etc/vsftpd.conf file with the following settings:


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

lrwxrwxrwx 1 root   root  12 Feb 28 23:04 fb -> /var/opt/fb/

The issue I am having is, is that I need only read access for the group "godatafeed" to the symbolic link, currently it is only set for root access.  But I did notice that the last permissions group "o (other/everyone)" is set for rwx, but I can get access to the fb folder when ftp'ing in.  I have the home directory set as:

useradd godatafeed -d /var/opt/godatafeed/ -s /bin/false

I can successfully log in with the username for ftp and browse the home directory, but I can't get to the "fb" directory.

How do I set the permissions correctly so only the root of the folder /var/opt/godatafeed just has read only permissions, as well as getting access to the "fb" symbolic link inside of the "godatafeed" folder?  

Thank you

---

### Post by Return Privacy on 2012-06-13
I can't help, but I have the exact same question! I want to allow the user to upload to 1 specific directory ONLY. I've got vsftpd working, but when the user uploads to it, it simply puts the files in the /home directory.I need them to upload to /media/2ndDrive/FTP, which is actually the second hard drive in the computer. Can someone help explain this?

---

