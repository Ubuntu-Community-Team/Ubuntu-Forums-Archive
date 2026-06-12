---
title: "VSFTPD with NIS environment doesn't work"
date: 2011-04-11
forum: Server Platforms
---

### Post by Du, Wei on 2011-04-11
Hi,
 
I installed Ubuntu 10.04 64bit server on DELL R710 server recently.
 
The basic:
 
[System Model] --- PowerEdge R710
 
[Ubuntu] --- 
 
root@pek-mcbuild2:~# cat /proc/version
Linux version 2.6.32-21-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010
root@pek-mcbuild2:~# uname -ar
Linux pek-mcbuild2 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux
 
The package:
 
root@pek-mcbuild2:~# dpkg -l | grep vsftp
ii vsftpd 2.2.2-3ubuntu6.1 lightweight, efficient FTP server written fo
 
 
root@pek-mcbuild2:~# dpkg -l | grep nis
ii nis 3.17-31 clients and daemons for the Network Informat
 
root@pek-mcbuild2:~# dpkg -l | grep portmap
ii portmap 6.0.0-1ubuntu2.1 RPC port mapper
 
root@pek-mcbuild2:~# dpkg -l | grep autofs
ii autofs 5.0.4-3.1ubuntu5.1 dummy transitional package from autofs to au
ii autofs5 5.0.4-3.1ubuntu5.1 kernel-based automounter for Linux, version
 
 
Files configured:
 
/etc/hosts
 
/etc/yp.conf
 
/etc/nsswitch.conf
 
passwd: files nis
group: files nis
shadow: files nis
hosts: files dns nis
automount: files nis
 
/etc/resolv.conf
 
network-mananger was uninstalled.
 
/etc/network/interfaces
 
/etc/auto.master
 
NIS and Automount work very well
 
Then I configured /etc/vsftpd.conf as below:
 
 
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
 
Created ftp user in /etc/passwd (which wasn't created by default)
 
Restarted vsftpd service.
 
Well the ftp and anonymous can login normally. Following created local users can login too. But any NIS user can't as below:
 
C:\Documents and Settings\wdu>ftp pek-mcbuild2
Connected to pek-mcbuild2.wrs.com.
220 (vsFTPd 2.2.2)
User (pek-mcbuild2.wrs.com:(none)): wdu
331 Please specify the password.
Password:
do_ypcall: clnt_call: RPC: Unable to send; errno = Network is unreachable
500 OOPS: cannot locate user entry:wdu
500 OOPS: priv_sock_get_cmd
Connection closed by remote host.
 
Can anyone help me? Thank you very much.

---

### Post by Du, Wei on 2011-04-12
No responese? Did I do something wrong or this issue is not supported here?:confused:

---

