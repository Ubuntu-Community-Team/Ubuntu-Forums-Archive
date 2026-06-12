---
title: "wu-ftpd (wuarchive-ftpd) for 13.10"
date: 2014-01-08
forum: Server Platforms
---

### Post by rmstock2 on 2014-01-08
I built wu-ftpd-2.6.2 on ubuntu 13.10 i386 and amd64. Together with the package 
anonftp_4.0-10ubuntu  you create a full chrooted environment for a anonymous ftp-server.
Download is at [ftp://ftp.crashrecovery.org/pub/linux/wuftpd/ubuntu1310/](ftp://ftp.crashrecovery.org/pub/linux/wuftpd/ubuntu1310/)

```
total 1472
drwxr-xr-x 2 root root   4096 Jan  8 19:12 ./
drwxr-xr-x 8 root root   4096 Jan  8 17:32 ../
-rw-r--r-- 1 root root   2162 Jan  8 15:42 anonftp_4.0-10ubuntu_amd64.deb
-rw-r--r-- 1 root root   2130 Jan  8 17:23 anonftp_4.0-10ubuntu_i386.deb
-rw-r--r-- 1 root root  30720 Jan  8 17:23 anonftp-4.0-10ubuntu.sdeb
-rw-r--r-- 1 root root  27016 Jan  8 02:37 compress_4.0-2ubuntu_amd64.deb
-rw-r--r-- 1 root root  25466 Jan  8 17:18 compress_4.0-2ubuntu_i386.deb
-rw-r--r-- 1 root root  40960 Jan  8 17:18 compress-4.0-2ubuntu.sdeb
-rw-r--r-- 1 root root 245760 Jan  8 17:16 libtermcap-2.0.8-37ubuntu.sdeb
-rw-r--r-- 1 root root  23858 Jan  8 03:52 libtermcap2_2.0.8-37ubuntu_amd64.deb
-rw-r--r-- 1 root root  23464 Jan  8 17:16 libtermcap2_2.0.8-37ubuntu_i386.deb
-rw-r--r-- 1 root root  25784 Jan  8 03:52 libtermcap2-dev_2.0.8-37ubuntu_amd64.deb
-rw-r--r-- 1 root root  23228 Jan  8 17:16 libtermcap2-dev_2.0.8-37ubuntu_i386.deb
-rw-r--r-- 1 root root   1059 Jan  8 19:12 MD5SUM
-rw-r--r-- 1 root root   5080 Jan  8 19:12 README.inst
-rw-r--r-- 1 root root   1162 May 29  2012 README.sdeb
-rw-r--r-- 1 root root 285196 Jan  8 15:53 wu-ftpd-crash_2.6.2-11.1204.1ubuntu_amd64.deb
-rw-r--r-- 1 root root 263878 Jan  8 17:21 wu-ftpd-crash_2.6.2-11.1204.1ubuntu_i386.deb
-rw-r--r-- 1 root root 440320 Jan  8 17:21 wu-ftpd-crash-2.6.2-11.1204.1ubuntu.sdeb
```

```
81be97768b270af48c63ee656da14bf0  anonftp_4.0-10ubuntu_amd64.deb
376bb77d7d4d1c9574369eeb186776b9  anonftp_4.0-10ubuntu_i386.deb
134cf63e3e8127d5ff407f3239040d02  anonftp-4.0-10ubuntu.sdeb
9ad030a790f118a2e20b8ea78e88398d  compress_4.0-2ubuntu_amd64.deb
5ff11f79a5bd960825a9aec4e7f662e0  compress_4.0-2ubuntu_i386.deb
d770f93b1e64d35dd7aa14a5e76e6b0a  compress-4.0-2ubuntu.sdeb
f97467843893b738969570ba576983c3  libtermcap-2.0.8-37ubuntu.sdeb
e2e90382e24cf3bb2b3c374deac409d0  libtermcap2_2.0.8-37ubuntu_amd64.deb
12051c497eae4f5fc9f5f2d56f15fba4  libtermcap2_2.0.8-37ubuntu_i386.deb
9a5d496605151b112ca3d8df0fb606c5  libtermcap2-dev_2.0.8-37ubuntu_amd64.deb
20275126ceebdf197c6a912159be2f84  libtermcap2-dev_2.0.8-37ubuntu_i386.deb
4d35ac773b03650b48f04ce4992356b4  README.inst
f8e33a5044b462757d41a9893286f7d0  README.sdeb
9648c6a3e10209c0bfe7de4cb7762bb7  wu-ftpd-crash_2.6.2-11.1204.1ubuntu_amd64.deb
591fcd820ea0d6fbe6d710f4d8da6020  wu-ftpd-crash_2.6.2-11.1204.1ubuntu_i386.deb
87bb52fc56e57f2ba9eb2196e1457ba8  wu-ftpd-crash-2.6.2-11.1204.1ubuntu.sdeb
```

[B]INSTALLATION
[/B]
1. install libtermcap2_2.0.8-37ubuntu_amd64.deb
2. install compress_4.0-2ubuntu_amd64.deb
2a. You might want to remove /usr/bin/zcmp, /usr/bin/zmore /usr/bin/zdiff
   and /usr/bin/zcat after installing compress as they interfere with
   /bin/zcmp, /bin/zmore, /bin/zdiff and /usr/bin/zcat from gzip :

root@ubu1310:~# **rm /usr/bin/zcmp /usr/bin/zmore /usr/bin/zdiff /usr/bin/zcat**

3. install xinetd
   apt-get install xinetd
4. install wu-ftpd-crash_2.6.2-11.1204.1ubuntu_amd64.deb

  root@ubu1310:~# **dpkg -i wu-ftpd-crash_2.6.2-11.1204.1ubuntu_amd64.deb**
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 35268 package 'libtermcap2':
 missing maintainer
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 35269 package 'libtermcap2':
 missing maintainer
dpkg: warning: parsing file '/var/lib/dpkg/tmp.ci/control' near line 19 package 'wu-ftpd-crash':
 missing maintainer
Selecting previously unselected package wu-ftpd-crash.
(Reading database ... 195151 files and directories currently installed.)
Unpacking wu-ftpd-crash (from wu-ftpd-crash_2.6.2-11.1204.1ubuntu_amd64.deb) ...
Setting up wu-ftpd-crash (2.6.2-11.1204.1ubuntu) ...
Generating a 1024 bit RSA private key
............++++++
...........................................................++++++
writing new private key to 'private/ftpd-rsa-key.pem'
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:**US**
State or Province Name (full name) [Some-State]:**VA**
Locality Name (eg, city) []:**Hampton**
Organization Name (eg, company) [Internet Widgits Pty Ltd]:
Organizational Unit Name (eg, section) []:**Transfer Dept.**
Common Name (e.g. server FQDN or YOUR name) []:**Joe Store**
Email Address []**:jstore@domain.com**
Processing triggers for man-db ...
root@ubu1310:~#

5. install anonftp_4.0-10ubuntu_amd64.deb , where the first time there
   will be a small error (i skip the `missing maintainer' warnings here):

root@ubu1310:~# **dpkg -i anonftp_4.0-10ubuntu_amd64.deb**
Selecting previously unselected package anonftp.
(Reading database ... 195227 files and directories currently installed.)
Unpacking anonftp (from anonftp_4.0-10ubuntu_amd64.deb) ...
Setting up anonftp (4.0-10ubuntu) ...
usermod: no changes
-- glibc
-- ld-linux
-- fileutils
-- cpio
-- tar
-- gzip
-- libtermcap
-- ncompress
-- anonftp
dpkg: error processing anonftp (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 anonftp
root@ubu1310:~#

   remove the PACKAGE AND INSTALL again :

root@ubu1310:~# **dpkg --purge anonftp**
Removing anonftp ...
Purging configuration files for anonftp ...
dpkg: warning: while removing anonftp, directory '/var/ftp/etc' not empty so not removed
dpkg: warning: while removing anonftp, directory '/var/ftp/lib64' not empty so not removed
dpkg: warning: while removing anonftp, directory '/var/ftp/bin' not empty so not removed
dpkg: warning: while removing anonftp, directory '/var/ftp/lib/x86_64-linux-gnu' not empty so not removed
root@ubu1310:~# **cd /var/ftp**
root@ubu1310:/var/ftp#** ll**
total 24
drwxr-xr-x  6 root root 4096 jan  8 18:45 ./
drwxr-xr-x 14 root root 4096 jan  8 18:34 ../
d--x--x--x  2 root root 4096 jan  8 18:37 bin/
d--x--x--x  2 root root 4096 jan  8 18:45 etc/
drwxr-xr-x  3 root root 4096 jan  8 18:37 lib/
drwxr-xr-x  2 root root 4096 jan  8 18:37 lib64/
root@ubu1310:/var/ftp# **rm -rf ***
root@ubu1310:/var/ftp# **cd**
root@ubu1310:~# **dpkg -i anonftp_4.0-10ubuntu_amd64.deb**
Selecting previously unselected package anonftp.
(Reading database ... 195227 files and directories currently installed.)
Unpacking anonftp (from anonftp_4.0-10ubuntu_amd64.deb) ...
Setting up anonftp (4.0-10ubuntu) ...
usermod: no changes
-- glibc
-- ld-linux
-- fileutils
-- cpio
-- tar
-- gzip
-- libtermcap
-- ncompress
-- anonftp
root@ubu1310:~#

   Your installation of wu-ftpd-crash is ready :

[acer20:stock](~)$** ftp u30**
Connected to u30.
220 ubu1310 FTP server (Version wu-2.6.2-11.1204.1ubuntu) ready.
504 AUTH GSSAPI not supported.
Name (u30:stock): **ftp**
331 Guest login ok, send your complete e-mail address as password.
Password:
230 Guest login ok, access restrictions apply.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> **dir**
227 Entering Passive Mode (192,168,178,30,162,128)
150 Opening ASCII mode data connection for directory listing.
total 40
d--x--x--x   2 root     root         4096 Jan  8 17:49 bin
d--x--x--x   2 root     root         4096 Jan  8 17:49 etc
drwxr-xr-x   3 root     root         4096 Jan  8 17:49 lib
drwxr-xr-x   2 root     root         4096 Jan  8 17:49 lib64
drwxr-xr-x   2 root     1001         4096 Jan  8 14:42 pub
226 Transfer complete.
ftp> **quit**
[acer20:stock](~)$

Robert M. Stockmann
Wed Jan  8 19:12:22 CET 2014

---

