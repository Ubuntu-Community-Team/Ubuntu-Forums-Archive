---
title: "Fail2 ban support for Ubuntu 6.06.1 LTS"
date: 2010-12-28
forum: Server Platforms
---

### Post by kartook on 2010-12-28
Hi all , 

Advance thanks to all , 

I install fail2ban on my too old server for security reasons . I am getting error message .

Few Out put from my Box 

```


root@LABPBX-01:~# sudo ls -l /var/run/fail2ban/
total 4
-rw------- 1 root root 6 2010-12-28 17:19 fail2ban.pid
srwx------ 1 root root 0 2010-12-28 17:19 fail2ban.sock
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~# sudo ls -l /var/run/fail2ban/ -d
**[COLOR=Blue]drwxr-xr-x 2 root root 80 2010-12-28 17:19 /var/run/fail2ban/[/COLOR]**
root@LABPBX-01:~#

root@LABPBX-01:~#
root@LABPBX-01:~# time sudo /etc/init.d/fail2ban start
[B][COLOR=Red]/etc/init.d/fail2ban: line 13: /etc/init.d/functions: No such file or directory
Starting fail2ban: /etc/init.d/fail2ban: line 36: echo_success: command not found[/COLOR][/B]


real    0m0.027s
user    0m0.010s
sys     0m0.020s
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~# time sudo /etc/init.d/fail2ban restart
[B][COLOR=Red]/etc/init.d/fail2ban: line 13: /etc/init.d/functions: No such file or directory
Stopping fail2ban: rm: cannot remove `/var/lock/subsys/fail2ban': Is a directory
/etc/init.d/fail2ban: line 54: echo_success: command not found

Starting fail2ban: /etc/init.d/fail2ban: line 36: echo_success: command not found[/COLOR][/B]


real    0m1.466s
user    0m0.330s
sys     0m0.040s
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~# uname -a
[COLOR=Blue]**Linux LABPBX-01 2.6.15-26-server #1 SMP Thu Aug 3 04:09:15 UTC 2006 i686 **[/COLOR]GNU/Linux
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~# lsb_release -dcs
[COLOR=Blue]**Ubuntu 6.06.1 LTS**[/COLOR]
dapper
root@LABPBX-01:~#
root@LABPBX-01:~#
root@LABPBX-01:~# apt-cache policy fail2ban
[B][COLOR=Blue]fail2ban:
  Installed: 0.6.0-3[/COLOR][/B]
  Candidate: 0.6.0-3
  Version table:
 *** 0.6.0-3 0
        500 http://in.archive.ubuntu.com dapper/universe Packages
        100 /var/lib/dpkg/status
root@LABPBX-01:~#
```

---

### Post by Waappu on 2010-12-28
Hi,

I do not have solution for you, sorry.
If you look security, you should upgrade your server OS.

---

### Post by Vegan on 2010-12-28
You might want to consider an new machine using a new version of Linux server.

---

### Post by windependence on 2010-12-28
Dudes, telling him to upgrade because YOU think latest and greatest is best is not helping him with the problem.
 
To the OP, your startup script for fail2ban is messed up, and it is not starting. You may want to completely remove fail2ban and then re-install it if you don't know how to fix the startup script or simply don't want to go through the hassle.
 
-Tim

---

### Post by windependence on 2010-12-28
This appears to be an SELinux bug. If you have SELinux enabled, try disabling it. 
 
To disable the SELinux permanently, modify the /etc/selinux/config and set the SELINUX=disabled as shown below. One you make any changes to the /etc/selinux/config, reboot the server for the changes to be considered.
```
 
# cat /etc/selinux/config
SELINUX=disabled
SELINUXTYPE=targeted
SETLOCALDEFS=0

```
 
-Tim

---

### Post by kartook on 2010-12-28
I love to THANKS for all friends :). :popcorn:=D>\\:D/

I am going to check today and let you know the status . 


This is the server i am using for more than 3 years without any trouble . Really i much impressed this server setup and don't want to disturb .

For security reasons i need to installing fail2ban .  

[COLOR=Blue]**NOTE : **[/COLOR]previously one of member try to install fail2ban through source  file ](*,). really i am not aware of this :oops: and i tried to install via apt-get and configured as what i need .

I doubt that is the  one messed up this issue .#-o

---

### Post by Thirtysixway on 2010-12-30
> **Waappu said:**
> Hi,

I do not have solution for you, sorry.
If you look security, you should upgrade your server OS.

6.06 is still supported..

---

### Post by kartook on 2011-01-12
> **windependence said:**
> This appears to be an SELinux bug. If you have SELinux enabled, try disabling it. 
 
To disable the SELinux permanently, modify the /etc/selinux/config and set the SELINUX=disabled as shown below. One you make any changes to the /etc/selinux/config, reboot the server for the changes to be considered.
```
 
# cat /etc/selinux/config
SELINUX=disabled
SELINUXTYPE=targeted
SETLOCALDEFS=0

```-Tim

root@C$$tSrv:~# cat /etc/selinux/config
cat: /etc/selinux/config: No such file or directory
root@C$$tSrv:~#

---

### Post by kartook on 2011-01-12
simply i like to remove the Fail2ban  from my server . 

apt-get remove fail2ban -----> already i did 

shows Error : 

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  fail2ban
0 upgraded, 0 newly installed, 1 to remove and 90 not upgraded.
Need to get 0B of archives.
After unpacking 246kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 36765 files and directories currently installed.)
Removing fail2ban ...
[COLOR=Red]/etc/init.d/fail2ban: line 13: /etc/init.d/functions: No such file or directory
Stopping fail2ban: /etc/init.d/fail2ban: line 59: echo_failure: command not found[/COLOR]

---

