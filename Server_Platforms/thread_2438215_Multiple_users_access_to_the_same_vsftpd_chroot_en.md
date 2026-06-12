---
title: "Multiple users access to the same vsftpd chroot environment in server 18.04"
date: 2020-03-07
forum: Server Platforms
---

### Post by desesperado on 2020-03-07
Hi all.

In a Ubuntu server:```
~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:        18.04
Codename:       bionic
4.15.0-88-generic
```

**Is it possible to have multiple remote users accessing the same vstfpd chroot environment?**

I have the following users defined in Ubuntu Server 18.04:```
~$ ls -la /home
total 28
drwxr-xr-x  7 root          root          4096 Mar  6 17:17 .
drwxr-xr-x 25 root          root          4096 Mar  4 15:06 ..
drwxr-xr-x  2 Acap          Acap          4096 Mar  6 17:17 Acap
drwxr-xr-x  5 administrator administrator 4096 Mar  6 17:08 administrator
drwxr-xr-x  2 Dgaiec        Dgaiec        4096 Mar  6 17:25 Dgaiec
drwxr-xr-x  4 ipt           ipt           4096 Feb 26 18:34 ipt
drwxr-xr-x  5 sivhappftp    sivhappftp    4096 Mar  6 17:06 sivhappftp
```My vsftpd.conf file is the following:```
~$ cat /etc/vsftpd.conf      
listen=YES
#listen_ipv6=NO
connect_from_port_20=YES
  
anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES
local_umask=022
user_sub_token=$USER
local_root=/home/$USER/sivh
allow_writeable_chroot=YES
secure_chroot_dir=/var/run/vsftpd/empty
  
pam_service_name=vsftpd
  
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=45000
  
userlist_enable=YES
userlist_file=/etc/vsftpd.userlist
userlist_deny=NO
```The vsftpd.userlist is:```
~$ cat /etc/vsftpd.userlist          
sivhappftp
Dgaiec
Acap
```
My query is the following, how to I get to allow the **Dgaiec** and **Acap** users access the sivhappftp chroot enviroment? I don't want, when they login to the server, to enter their respective chroots environments but to navigate directly into```
~$ ls -la /home/sivhappftp/sivh/
total 20
drwxrwxrwx 5 sivhappftp sivhappftp 4096 Mar  6 16:16 .
drwxr-xr-x 5 sivhappftp sivhappftp 4096 Mar  6 17:06 ..
drwxrwxrwx 2 sivhappftp sivhappftp 4096 Mar  6 16:11 acap
drwxrwxrwx 2 sivhappftp sivhappftp 4096 Mar  6 16:11 dgaiec
drwxrwxrwx 2 sivhappftp sivhappftp 4096 Mar  6 16:11 igfej
```The only interaction that the three users have with the server is to upload and download files. 

The sivhappftp user feeds both **/home/sivhappftp/sivh/acap/** folder (for the Acap user) and **/home/sivhappftp/sivh/dgaiec/** folder (for the Dgaiec user) with files and both Acap and Dgaiec will download the files from for those respective folders.

---

### Post by desesperado on 2020-03-08
bump

---

### Post by TheFu on 2020-03-08
No clue, we stopped using anything except sftp decades ago, but
```

**drwxrwxrwx** 5 sivhappftp sivhappftp 4096 Mar  6 16:16 .
drwxr-xr-x 5 sivhappftp sivhappftp 4096 Mar  6 17:06 ..
**drwxrwxrwx** 2 sivhappftp sivhappftp 4096 Mar  6 16:11 acap
**drwxrwxrwx** 2 sivhappftp sivhappftp 4096 Mar  6 16:11 dgaiec
**drwxrwxrwx** 2 sivhappftp sivhappftp 4096 Mar  6 16:11 igfej
```
are crazy, non-secure, permissions.

Anyone on the machine can delete all those directories and all files. ANYONE.  The groups should be specific to each user and permissions for any upload directory shouldn't allow anyone read-access, not even the userid allowed to upload.  This is standard FTP upload security.

---

### Post by desesperado on 2020-03-08
Thanks for your input, The Fu. I'll get those permissions corrected.

Bur regarding my query if it's possible to habilitate the three users with access to the same chroot environment? Even though you're clueless, do you think it's possible?

Can you think of another way of achieving it, other than having the three accessing said chroot environment?

---

### Post by desesperado on 2020-03-09
Solved it.

The solution was to mount the needed directory using the **--bind** parameter. So, what I did was:```
mkdir /home/ftp_user/sivh/
sudo mount --bind /home/sivhappftp/sivh/ftp_user/ /home/ftp_user/sivh/
```After this each ftp user will be able to see the needed files in his home directory and use them in his ftp client as if they were local files.

Made this configuration permanent including a line, for each, in **/etc/fstab**:```
/home/sivhappftp/sivh/ftp_user/   /home/ftp_user/sivh/      none    bind    0       0
```

Of course the permissions, mentioned by The Fu, were corrected```
~$ ls -la /home/sivhappftp/
total 12
drwxr-xr-x 3 root   root    4096 Mar  9 11:35 .
drwxr-xr-x 8 root   root    4096 Mar  9 16:24 ..
dr-xr-xr-x 5 nobody nogroup 4096 Mar  9 16:11 sivh

~$ ls -la /home/sivhappftp/sivh/
total 32
dr-xr-xr-x 5 nobody     nogroup    4096 Mar  9 16:11 .
drwxr-xr-x 3 root       root       4096 Mar  9 11:35 ..
drwxrwxrwx 3 root       root       4096 Mar  9 12:40 acap
-rw-r--r-- 1 sivhappftp sivhappftp  220 Mar  9 11:35 .bash_logout
-rw-r--r-- 1 sivhappftp sivhappftp 3771 Mar  9 11:35 .bashrc
drwxrwxrwx 8 root       root       4096 Mar  9 15:16 dgaiec
drwxrwxrwx 5 root       root       4096 Mar  9 16:12 itij
-rw-r--r-- 1 sivhappftp sivhappftp  807 Mar  9 11:35 .profile

```

---

### Post by TheFu on 2020-03-09
```
drwxrwxrwx 3 root       root       4096 Mar  9 12:40 acap
drwxrwxrwx 8 root       root       4096 Mar  9 15:16 dgaiec
drwxrwxrwx 5 root       root       4096 Mar  9 16:12 itij
```

are wrong.  Don't use 777 permissions. You'll need to set the groups correctly and use either 775 or 770 permissions.

---

