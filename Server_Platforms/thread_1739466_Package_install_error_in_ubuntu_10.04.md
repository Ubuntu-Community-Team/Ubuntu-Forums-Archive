---
title: "Package install error in ubuntu 10.04"
date: 2011-04-26
forum: Server Platforms
---

### Post by rohitnagare on 2011-04-26
Hi Good morning,

I have installed Ubuntu 10.04 LTS server 32 Bit. Now have to install FTP package in my sever i dont have internet connection but i have downloaded the vsftpd_2.0.4-0ubuntu4.1_i386.deb file but while installing i get the following error.
# dpkg -i vsftpd_2.0.4-0ubuntu4.1_i386.deb
(Reading database ... 42228 files and directories currently installed.)
Unpacking vsftpd (from vsftpd_2.0.4-0ubuntu4.1_i386.deb) ...
dpkg: error processing vsftpd_2.0.4-0ubuntu4.1_i386.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
Errors were encountered while processing:
 vsftpd_2.0.4-0ubuntu4.1_i386.deb

Need Help to install VSFTPD package on my ubuntu server.

Regards
Rohit

---

### Post by mikewhatever on 2011-04-26
You may need to re-download the package, and to make sure it's not corrupted, check it with md5sum.

---

### Post by rohitnagare on 2011-04-26
Hi Mike,

Thanks for the reply we have download many packages from net and tried to installed with 
dpkg -i .deb but giving corruption error for all deb files while installing is there any other command to install packages. Because i am not  much familiar with Ubunt.

---

### Post by mikewhatever on 2011-04-26
It looks like the package version of vsftpd you've been trying to install (2.0.4-0ubuntu4.1) is for Dapper (Ubuntu 6.06). Lucid has a different version - [2.2.2-3ubuntu6.1]("http://packages.ubuntu.com/lucid/vsftpd").

---

### Post by rohitnagare on 2011-04-26
Hi mike,

i have downloaded the package as u said but same error.

# dpkg -i vsftpd_2.2.2-3ubuntu6.1_i386.deb
(Reading database ... 42228 files and directories currently installed.)
Unpacking vsftpd (from vsftpd_2.2.2-3ubuntu6.1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg: error processing vsftpd_2.2.2-3ubuntu6.1_i386.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 vsftpd_2.2.2-3ubuntu6.1_i386.deb

Regards
Rohit

---

### Post by mikewhatever on 2011-04-26
Not sure really. I'll try searching for those errors, hope it turns up something useful.

---

### Post by rohitnagare on 2011-04-26
Hi mike,

I have downloaded the folling deb file from other machine and installed now getting this error

 dpkg -i vsftpd_2.2.2-3ubuntu6.1_i386.deb
(Reading database ... 42281 files and directories currently installed.)
Preparing to replace vsftpd 2.2.2-3ubuntu6.1 (using vsftpd_2.2.2-3ubuntu6.1_i386.deb) ...
Unpacking replacement vsftpd ...
dpkg: dependency problems prevent configuration of vsftpd:
 vsftpd depends on ssl-cert (>= 1.0-11ubuntu1); however:
  Package ssl-cert is not installed.
 vsftpd depends on update-inetd; however:
  Package update-inetd is not installed.
dpkg: error processing vsftpd (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 vsftpd


Please help

Regards
Rohit

---

### Post by mikewhatever on 2011-04-26
Well, package dependencies must be installed first. Normally, the package manager does all the resolving and downloading for you, but that requires an internet connection.

---

### Post by rubylaser on 2011-04-26
These are the packages, that it depends on.

[http://packages.ubuntu.com/lucid/net/vsftpd]("http://packages.ubuntu.com/lucid/net/vsftpd")

All of them must be installed for it to install and work properly.  My I ask why your proposed FTP server doesn't have access to the internet?

---

### Post by Vegan on 2011-04-26
I use vsftp and I installed with the usual apt-get fine

try that

sudo apt-get install vsftpd

---

