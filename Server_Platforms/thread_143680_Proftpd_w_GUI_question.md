---
title: "Proftpd w/ GUI question"
date: 2006-03-12
forum: Server Platforms
---

### Post by Griff on 2006-03-12
This server was initially set up to provide easy access for me and some friends files from this comp, but I now want to change the location to which ftp users are directed when logging in.  To be specific, instead of sending users to the default root of /home/ftp I want everyone to be put on my external HDD: /media/"WD USB 2"/Media.  I tried changing the root directories under the users and server tabs (under gProftpd), but I am getting the notorious 530 loggin error if I try to connect with one of these new users.  I'm guessing maybe there is a permission problem here but am not sure of what to do.  Any help appreciated.
Griff

---

### Post by frodon on 2006-03-13
Try to set the home directory of the users you use for the ftp to this directory and check that your external drive have the good rights (755 for a download directory).
You could also post your proftpd.conf file here, it could be helpful.

---

### Post by Griff on 2006-03-13
[QUOTE=frodon]Try to set the home directory of the users you use for the ftp to this directory and check that your external drive have the good rights (755 for a download directory).
You could also post your proftpd.conf file here, it could be helpful.[/QUOTE]
I set the home directory of the users to this directory, but no success.  I do not understand what you mean by "check that your external drive have the good rights (755)".  Here is my .conf file
```
ServerType standalone
DefaultServer on
Umask 022
ServerName "70.171.39.106"
ServerIdent on "My FTPD"
Bind "70.171.39.106"
ServerAdmin stevejworkman@gmail.com
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49148 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
User nobody
Group nogroup
DirFakeUser off nobody
DirFakeGroup off nobody
DefaultTransferMode binary
AllowForeignAddress on
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 2000
TransferRate STOR 40
TransferRate STOU 40
TransferRate APPE 40
SystemLog /var/log/secure
#gp_random_username_length 6
#gp_random_password_length 6
#gp_randomize_case lower
#gp_useradd_root_path /media/"WD USB 2"/Media
#gp_useradd_upload_path /media/"WD USB 2"/Media/upload
#gp_html_path /var/www/ftp.html
#gp_welcome_name welcome.msg
<IfModule mod_tls.c>
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol TLSv1
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gproftpd/gproftpd.pem
</IfModule>
<Limit LOGIN>
  AllowUser nate
  DenyALL
</Limit>

<Anonymous /media/"WD USB 2"/Media>
User nate
Group nate
AnonRequirePassword on
MaxClients 3 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayFirstChdir .msg
AllowOverwrite off
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
<Limit ROOT_DIR_ALLOW RETR LIST NLST MDTM SIZE STAT CWD XCWD PWD XPWD CDUP XCUP>
 AllowAll
</Limit>
<Limit ROOT_DIR_DENY DELE APPE STOR STOU SITE_CHMOD SITE_CHGRP RNFR RNTO MKD XMKD RMD XRMD>
 DenyAll
</Limit>
<Directory /media/"WD USB 2"/Media/upload>
AllowOverwrite on
<Limit UPLOAD_DIR_ALLOW LIST NLST  STOR STOU  APPE  RETR  STAT  MDTM  PWD XPWD  SIZE  CWD XCWD  SITE >
 AllowAll
</Limit>
<Limit UPLOAD_DIR_DENY RNFR RNTO  DELE  MKD XMKD  RMD XRMD  SITE_CHMOD  SITE_CHGRP  CDUP XCUP >
 DenyAll
</Limit>
</Directory>
</Anonymous>

```

---

### Post by frodon on 2006-03-14
I mean that proftpd never overwrites the system rights therefore if the system rights of your external drive are too restrictive compared to the rights you set in your proftpd.conf file you could get this kind of errors.
So checks what are the system rights of your external partition and try to modify them if they seem too restrictive.
You can change the system rights with the "chmod" command.

---

### Post by Griff on 2006-03-15
Ok.  So I read up on the 'chmod' command at the wiki and used it on a few unimportant files.  However, I am still unable to change permission settings on the external drive.  I tried using the user (stephen), sudo, and root, but none are able to change the settings.  I don't recieve an error; it's just that nothing happens.  Here's a printout: ```

stephen@ubuntu:/media$ ls -l
total 66
lrwxrwxrwx  1 root    root        6 2005-11-29 11:30 cdrom -> cdrom0
drwxr-xr-x  2 root    root     4096 2005-11-29 11:30 cdrom0
dr-xr-xr-x  1 root    root     2048 2006-01-13 10:52 cdrom1
drwxr-xr-x  2 root    root     4096 2005-11-29 11:30 cdrom2
lrwxrwxrwx  1 root    root        7 2005-11-29 11:30 floppy -> floppy0
drwxr-xr-x  2 root    root     4096 2005-11-29 11:30 floppy0
dr-x------  1 root    root    12288 2006-03-13 14:11 hda1
drwxr-xr-x  4 root    root     8192 1969-12-31 19:00 hda3
drwx------  6 stephen stephen 32768 1969-12-31 19:00 WD USB 2
stephen@ubuntu:/media$ chmod o+rwx "WD USB 2"
stephen@ubuntu:/media$ ls -l
total 66
lrwxrwxrwx  1 root    root        6 2005-11-29 11:30 cdrom -> cdrom0
drwxr-xr-x  2 root    root     4096 2005-11-29 11:30 cdrom0
dr-xr-xr-x  1 root    root     2048 2006-01-13 10:52 cdrom1
drwxr-xr-x  2 root    root     4096 2005-11-29 11:30 cdrom2
lrwxrwxrwx  1 root    root        7 2005-11-29 11:30 floppy -> floppy0
drwxr-xr-x  2 root    root     4096 2005-11-29 11:30 floppy0
dr-x------  1 root    root    12288 2006-03-13 14:11 hda1
drwxr-xr-x  4 root    root     8192 1969-12-31 19:00 hda3
drwx------  6 stephen stephen 32768 1969-12-31 19:00 WD USB 2

```
I can't change group or other settings.  ' chmod 755 "WD USB 2" ' doesn't work either.  I also tried changing the owner to 'root' using 'sudo nautilus', but that doesn't work either.  Any ideas?
Thank you for your continued help.
Griff

---

### Post by frodon on 2006-03-15
What file system use your external harddrive : ext3, FAT32, NTFS ?
Maybe the automount feature mount your partition with too restrictive rights so you may have to mount your partition manually.
By the way, FAT32 and NTFS file systems don't support unix rights therefore chmod, chown, chgrp commands will not work with those file systems, the only way to set rights with NTFS and FAT32 file system is with the mount command.
If it's the case unmount your partition : ```
sudo umount /media/WD\ USB\ 2
```Then mount it manually following one of these 2 guides : 
[http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)
[http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

### Post by Griff on 2006-03-15
Following both guides I get the same error.  I've had to mount and unmount things before with no problem so I don't know what's going on here. :confused: 
```
stephen@ubuntu:~$ sudo mount /media/WD\ USB\ 2 /media/windows/ -t vfat -o iocharset=utf8,umask=000
mount: /media/WD USB 2 is not a block device

```

---

### Post by frodon on 2006-03-16
Ho, /media/WD\ USB\ 2 is not the name of your drive ! it's where you will mount the partition.
All the device names are under /dev, here the name of your partition will be /dev/***, to know the name of the partition use this command : ```
sudo fdisk -l
```Then thanks to the file sytem and size informations you will know the name of your partition then use this name for the mount command. It's also explained in the links i gave you.
If you have some problems to know the name of your partition post the output of the "sudo fdisk -l" command here.
Your mount command should look like that : ```
sudo mount /dev/*partition-name* /media/WD\ USB\ 2 -t vfat -o iocharset=utf8,umask=000
```

---

### Post by Griff on 2006-03-17
Well.  It looks as though everything is mounted properly and does so on boot up, but now I have a different problem.  I have the external drive mounted as described in your link in /media/windows.  Therefore I changed the root directory of the user to /media/windows/Media.  Media is the folder on the external drive that I want users directed to.  When trying to log in a user, I no longer get the '530 error'.  It now says 'connection refused'.  I have port 21 open for everyone on firestarter and port 21 forwarded to my comp via my router.  Any ideas?

---

### Post by Griff on 2006-03-17
It works!  I accidently 'scrolled down' the listening ftp port on the server earlier so it was listening to port 18 instead of 21.  Whoops.  Frodon I can't thank you enough for helping me through all this.  Thanks a ton!  You rock! =D>

---

