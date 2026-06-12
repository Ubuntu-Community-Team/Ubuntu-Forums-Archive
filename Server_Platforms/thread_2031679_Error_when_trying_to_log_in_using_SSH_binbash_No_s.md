---
title: "Error when trying to log in using SSH: /bin/bash: No such file or directory"
date: 2012-07-22
forum: Server Platforms
---

### Post by BlueZenith on 2012-07-22
Hi all,

I have a dedicated server running Ubuntu Server 12.04 64-bit. For a little more than a week now, I have been unable to log into it using SSH. The output I get is:

```
$ ssh xxxxxxx.com
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-26-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Sat Jul 14 21:49:44 CDT 2012

  System load:  0.46                Processes:           198
  Usage of /:   32.1% of 457.24GB   Users logged in:     0
  Memory usage: 64%                 IP address for eth0: xxx.xxx.xxx.xx
  Swap usage:   3%

  Graph this data and manage this system at https://landscape.canonical.com/

1 package can be updated.
0 updates are security updates.

Last login: Sun Jul 22 11:42:17 2012 from xxx.xx.xxx.xx
/bin/bash: No such file or directory
Connection to xxxxxxx.com closed.
```Note how the "System information" hasn't been updated since Sat Jul 14 21:49:44 CDT 2012 (which is probably about when this problem started).

The websites hosted on this server (using Apache, PHP and MySQL) are still running fine, and I can still do things on it with Virtualmin/Webmin/Usermin.

Using Webmin's built-in Java-based file manager, I have determined that /bin/bash does indeed exist, and that its permissions are 755 (allowing reading and execution by all users) and that the permissions for the /bin directory are 6755 (allowing reading and listing by all users).

I have also tried uploading the bash executable from my home desktop (also running Ubuntu 12.04 64-bit) to my home directory on the server and setting the shell to that by editing /etc/passwd, but that resulted in the same "No such file or directory" error for the bash path in my home directory.

Attempting to have SSH execute a command on the server rather than a login shell also yields the same error:

```
$ ssh xxxxxxx.com pwd
/bin/bash: No such file or directory
```Trying to log in as other users also didn't work.

Frankly, I'm at a loss.

If anyone has any ideas, please let me know! Thanks in advance.

-BZ

---

### Post by papibe on 2012-07-22
Hi BlueZenith. Welcome to the forums ):P

It looks like you tried to do chroot configuration, but something went wrong.

Could you post the content of this file?
```
/etc/ssh/sshd_config
```

Regards.

---

### Post by BlueZenith on 2012-07-22
> **papibe said:**
> Hi BlueZenith. Welcome to the forums ):P
Thank you papibe, and thanks for replying :)

> **papibe said:**
> It looks like you tried to do chroot configuration, but something went wrong.

Could you post the content of this file?
```
/etc/ssh/sshd_config
```
I can imagine that it looks that way, but I've never used chroot before in my life.

These are the contents of /etc/ssh/sshd_config on the server:
```
# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
```

---

### Post by BlueZenith on 2012-07-24
This has just got even more confusing, I think.

Setting /bin/bash as shell for my account, I get the following when I connect through SSH (omitting the system information and disconnect message which are the same every time):

```
/bin/bash: No such file or directory
```Similarly, with /bin/dash set as shell, I get:

```
/bin/dash: No such file or directory
```However, setting /bin/busybox as shell results in BusyBox's normal output when connecting through SSH:

```
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) multi-call binary.
Copyright (C) 1998-2009 Erik Andersen, Rob Landley, Denys Vlasenko
and others. Licensed under GPLv2.
See source distribution for full notice.

Usage: busybox [function] [arguments]...
   or: busybox --list[-full]
   or: function [arguments]...

    BusyBox is a multi-call binary that combines many common Unix
    utilities into a single executable.  Most people will create a
    link to busybox for each function they wish to use and BusyBox
    will act like whatever it was invoked as.

Currently defined functions:
    [, [[, acpid, addgroup, adduser, adjtimex, ar, arping, ash,
    awk, basename, blockdev, brctl, bunzip2, bzcat, bzip2, cal,
    cat, chgrp, chmod, chown, chroot, chvt, clear, cmp, cp, cpio,
    crond, crontab, cut, date, dc, dd, deallocvt, delgroup,
    deluser, df, diff, dirname, dmesg, dnsdomainname, dos2unix,
    dpkg, dpkg-deb, du, dumpkmap, dumpleases, echo, ed, egrep,
    eject, env, expand, expr, false, fbset, fdflush, fdisk, fgrep,
    find, fold, free, freeramdisk, fsck.minix, ftpget, ftpput,
    getopt, getty, grep, gunzip, gzip, head, hexdump, hostid,
    hostname, httpd, hwclock, id, ifconfig, ifdown, ifup, init,
    ionice, ip, ipcalc, kill, killall, klogd, last, length, less,
    linuxrc, ln, loadfont, loadkmap, logger, login, logname,
    logread, losetup, ls, lzcat, lzma, makedevs, md5sum, mdev,
    mesg, microcom, mkdir, mkfifo, mkfs.minix, mknod, mkswap,
    mktemp, more, mount, mt, mv, nameif, nc, netstat, nslookup,
    od, openvt, passwd, patch, pidof, ping, ping6, pivot_root,
    printf, ps, pwd, rdate, readlink, realpath, renice, reset,
    rev, rm, rmdir, route, rpm, rpm2cpio, run-parts, sed, seq,
    setkeycodes, sh, sha1sum, sha256sum, sha512sum, sleep, sort,
    start-stop-daemon, static-sh, strings, stty, su, sulogin,
    swapoff, swapon, switch_root, sync, sysctl, syslogd, tac,
    tail, tar, tee, telnet, telnetd, test, tftp, time, timeout,
    top, touch, tr, traceroute, traceroute6, true, tty, tunctl,
    udhcpc, udhcpd, umount, uname, uncompress, unexpand, uniq,
    unix2dos, unlzma, unxz, unzip, uptime, usleep, uudecode,
    uuencode, vconfig, vi, vlock, watch, watchdog, wc, wget,
    which, who, whoami, xargs, xz, xzcat, yes, zcat
```And symbolically linking /bin/sh to /bin/busybox and then setting /bin/sh as the shell results in a working BusyBox shell:

```
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.

$ 
```The built-in BusyBox commands (like ls and which) work fine, but I have so far been unable to find any executable that will run, except for the BusyBox executable itself:

```
$ which bash
/bin/bash
$ ls -l /bin/bash
-rwxr-xr-x    1 root     root        955024 Apr  3 10:58 /bin/bash
$ /bin/bash
-sh: /bin/bash: not found
``````
$ which ls
/bin/ls
$ ls -l /bin/ls
-rwxr-xr-x    1 root     root        105840 Mar 31 22:09 /bin/ls
$ /bin/ls
-sh: /bin/ls: not found
``````
$ which mysql
/usr/bin/mysql
$ ls -l /usr/bin/mysql
-rwxr-xr-x    1 root     root       3499664 Jun 21 18:29 /usr/bin/mysql
$ /usr/bin/mysql
-sh: /usr/bin/mysql: not found
``````
$ which busybox
/bin/busybox
$ ls -l /bin/busybox
-rwxr-xr-x    1 root     root       1827920 Apr 13 14:53 /bin/busybox
$ /bin/busybox
BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) multi-call binary.
Copyright (C) 1998-2009 Erik Andersen, Rob Landley, Denys Vlasenko
and others. Licensed under GPLv2.
See source distribution for full notice.

Usage: busybox [function] [arguments]...
   or: busybox --list[-full]
   or: function [arguments]...

    BusyBox is a multi-call binary that combines many common Unix
    utilities into a single executable.  Most people will create a
    link to busybox for each function they wish to use and BusyBox
    will act like whatever it was invoked as.

Currently defined functions:
    [, [[, acpid, addgroup, adduser, adjtimex, ar, arping, ash,
    awk, basename, blockdev, brctl, bunzip2, bzcat, bzip2, cal,
    cat, chgrp, chmod, chown, chroot, chvt, clear, cmp, cp, cpio,
    crond, crontab, cut, date, dc, dd, deallocvt, delgroup,
    deluser, df, diff, dirname, dmesg, dnsdomainname, dos2unix,
    dpkg, dpkg-deb, du, dumpkmap, dumpleases, echo, ed, egrep,
    eject, env, expand, expr, false, fbset, fdflush, fdisk, fgrep,
    find, fold, free, freeramdisk, fsck.minix, ftpget, ftpput,
    getopt, getty, grep, gunzip, gzip, head, hexdump, hostid,
    hostname, httpd, hwclock, id, ifconfig, ifdown, ifup, init,
    ionice, ip, ipcalc, kill, killall, klogd, last, length, less,
    linuxrc, ln, loadfont, loadkmap, logger, login, logname,
    logread, losetup, ls, lzcat, lzma, makedevs, md5sum, mdev,
    mesg, microcom, mkdir, mkfifo, mkfs.minix, mknod, mkswap,
    mktemp, more, mount, mt, mv, nameif, nc, netstat, nslookup,
    od, openvt, passwd, patch, pidof, ping, ping6, pivot_root,
    printf, ps, pwd, rdate, readlink, realpath, renice, reset,
    rev, rm, rmdir, route, rpm, rpm2cpio, run-parts, sed, seq,
    setkeycodes, sh, sha1sum, sha256sum, sha512sum, sleep, sort,
    start-stop-daemon, static-sh, strings, stty, su, sulogin,
    swapoff, swapon, switch_root, sync, sysctl, syslogd, tac,
    tail, tar, tee, telnet, telnetd, test, tftp, time, timeout,
    top, touch, tr, traceroute, traceroute6, true, tty, tunctl,
    udhcpc, udhcpd, umount, uname, uncompress, unexpand, uniq,
    unix2dos, unlzma, unxz, unzip, uptime, usleep, uudecode,
    uuencode, vconfig, vi, vlock, watch, watchdog, wc, wget,
    which, who, whoami, xargs, xz, xzcat, yes, zcat
```So BusyBox and Webmin can see these executables and show that they have the correct permissions, but when they are supposed to get executed, they somehow can't be found &#8212; except busybox, which must be special in some way that I can't identify.

I wondered what would happen if I tried to execute one of these (e.g., bash) without the executable permission set. This was the result:

```
$ cp /bin/bash .
$ ./bash
-sh: ./bash: not found
$ chmod -x bash
$ ./bash
-sh: ./bash: Permission denied
$ chmod +x bash
$ ./bash
-sh: ./bash: not found
```The problem doesn't just affect SSH, as shown by the mail error log (/var/log/mail.err), the last 10 lines of which are:

```
Jul 24 11:20:56 chicago master[2156]: fatal: master_spawn: exec /usr/lib/postfix/smtpd: No such file or directory
Jul 24 11:20:56 chicago master[2157]: fatal: master_spawn: exec /usr/lib/postfix/pickup: No such file or directory
Jul 24 11:21:57 chicago master[2196]: fatal: master_spawn: exec /usr/lib/postfix/smtpd: No such file or directory
Jul 24 11:21:57 chicago master[2197]: fatal: master_spawn: exec /usr/lib/postfix/pickup: No such file or directory
Jul 24 11:22:58 chicago master[2274]: fatal: master_spawn: exec /usr/lib/postfix/smtpd: No such file or directory
Jul 24 11:22:58 chicago master[2275]: fatal: master_spawn: exec /usr/lib/postfix/pickup: No such file or directory
Jul 24 11:23:59 chicago master[2672]: fatal: master_spawn: exec /usr/lib/postfix/smtpd: No such file or directory
Jul 24 11:23:59 chicago master[2673]: fatal: master_spawn: exec /usr/lib/postfix/pickup: No such file or directory
Jul 24 11:25:00 chicago master[2779]: fatal: master_spawn: exec /usr/lib/postfix/smtpd: No such file or directory
Jul 24 11:25:00 chicago master[2780]: fatal: master_spawn: exec /usr/lib/postfix/pickup: No such file or directory

```(Like the other executables mentioned before, /usr/lib/postfix/smtpd and /usr/lib/postfix/pickup do in fact exist and have the appropriate permissions.)

I am not aware of any change I have made that could have anything to do with this problem or was correlated with its beginning.

The package-manager log shows that the most recent package actions were upgrades of OpenJDK 6 and IcedTea 6, which happened days before the problem first occurred. 

I'm scared to restart the machine for fear that it won't properly boot at all with whatever problem is going on. My websites (one of which is absolutely mission-critical) are fortunately still running fine, but things clearly can't keep going on like this.

Any ideas, anyone?

---

### Post by spjackson on 2012-07-24
This is a bit of a guess. busybox is statically linked whereas bash, dash and other similar programs are dynamically linked. So it could be that some fundamental library has gone missing.

Does ```
ldd /bin/bash
``` give any clues? (Assuming ldd works!)

---

### Post by matt_symes on 2012-07-24
Hi
> 
So BusyBox ... can see these executables and show that they have  the correct permissions, but when they are supposed to get executed,  they somehow can't be found &#8212; except busybox, which must be special in  some way that I can't identify.This is not actually how busy bux works.
[FONT=monospace]
[/FONT]> BusyBox is a multi-call binary that combines many common Unix     utilities into a single executableBusybox contains all the commands to run (ls, chown, chmod....) within the executable itself. 

Busybox knows which commands to run because, usually, each call in busybox is a symlink. Obviously at the busybox command prompt each call into busybox will also work.

Internally, busybox will read the name of the symlink that called into it and, therefore, know which command to run. ie. which function within the busybox executable to run.

Your problem is not busybox being able to run the executables. The busybox is one exectuable containingt functions that implement the commands.

Check your $PATH.
Check PAM. 
Check out ldd as posted above. 
Commands will not run if libc cannot be loaded by an executable. (check permissions)
Check you library paths are accessible.
Check the libc symbolic links are intact.

EDIT: To make the above commentry on busybox clearer, read this...

(Ubuntu is on a different partition than the one i am currently using.....)

```

[matthew@matthew-aspire7450]~% ln -s /mnt/bin/busybox ls
[matthew@matthew-aspire7450]~% ls -l ~/ls
lrwxrwxrwx. 1 matthew matthew 16 Jul 24 18:31 /home/matthew/ls -> /mnt/bin/busybox
[matthew@matthew-aspire7450]~% ~/ls
Desktop              Dropbox              Public               index.html           my_storage           sshfs_media          test
Documents            Music                Templates            ls                   my_virtual_machines  storage
Downloads            Pictures             Videos               my_documents         sshfs_home           t
[matthew@matthew-aspire7450]~%
```Kind regards

---

### Post by BlueZenith on 2012-07-24
Thank you both for your advice! I've got it back to working. :grin:

I tried spjackson's suggestion, which didn't work on the server: ```
$ ldd
-sh: ldd: not found
``` (presumably because ldd itself has  dynamically linked dependencies), but running it locally on my home  desktop (which is set up mostly the same way) gave four file  paths:

```
$ ldd /bin/bash
    linux-vdso.so.1 =>  (0x00007fff2a7ff000)
    libtinfo.so.5 => /lib/x86_64-linux-gnu/libtinfo.so.5 (0x00007f2754708000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f2754504000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f2754146000)
    /lib64/ld-linux-x86-64.so.2 (0x00007f2754953000)
```The first three were present on the server, but the last one was not. It  turned out that the lib64 directory (as well as the lib32 directory)  that was present on my home system didn't exist on the server. So I  tarred my local lib32 and lib64 directories and uploaded/unpacked them using  Webmin's file manager, and now everything seems to be back to normal.

I'd sure like to know how those directories got deleted (or the lib64 one at least &#8212; I copied the lib32 one along just in case).

But more than that, I find it puzzling that the error messages seemed to suggest that  the executables themselves could not be found, rather than mentioning  the library that was actually missing. A message like ```
/bin/bash: Missing dynamic library: /lib64/ld-linux-x86-64.so.2
``` would have  been infinitely more useful than ```
/bin/bash: No such file or  directory
``` or ```
fatal: master_spawn: exec /usr/lib/postfix/smtpd: No such file or directory
``` and would have saved many hours of troubleshooting in  this case. 

Would it be reasonable to suggest this as an idea for improvement somewhere?

---

### Post by papibe on 2012-07-24
May be a missconfigured or corrupted libc6 ?

Could you post the result of these commands?
```
apt-cache policy libc6

dpkg -L libc6
```
Regards.

---

### Post by matt_symes on 2012-07-24
Hi

> But more than that, I find it puzzling that the error messages seemed to  suggest that  the executables themselves could not be found, rather  than mentioning  the library that was actually missingIt means that either the executable cannot be found or a dependant dynamically loaded library. (ofcourse ther are other reasons for it as well)

Maybe not the best error message in the world :)

Kind regards

---

### Post by matt_symes on 2012-07-24
Hi

Just wanted to say...

Nice work [spjackson]("http://ubuntuforums.org/member.php?u=1128302"). Good call !!

Kind regards

---

### Post by BlueZenith on 2012-07-24
> **papibe said:**
> May be a missconfigured or corrupted libc6 ?

Could you post the result of these commands?
```
apt-cache policy libc6

dpkg -L libc6
```Regards.
Here are the results:

```
$ apt-cache policy libc6
libc6:
  Installed: 2.15-0ubuntu10
  Candidate: 2.15-0ubuntu10
  Version table:
 *** 2.15-0ubuntu10 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
``````
$ dpkg -L libc6
/.
/etc
/etc/ld.so.conf.d
/etc/ld.so.conf.d/x86_64-linux-gnu.conf
/lib
/lib/x86_64-linux-gnu
/lib/x86_64-linux-gnu/libcidn-2.15.so
/lib/x86_64-linux-gnu/libm-2.15.so
/lib/x86_64-linux-gnu/libc-2.15.so
/lib/x86_64-linux-gnu/libpcprofile.so
/lib/x86_64-linux-gnu/ld-2.15.so
/lib/x86_64-linux-gnu/libresolv-2.15.so
/lib/x86_64-linux-gnu/libnsl-2.15.so
/lib/x86_64-linux-gnu/libthread_db-1.0.so
/lib/x86_64-linux-gnu/librt-2.15.so
/lib/x86_64-linux-gnu/libmemusage.so
/lib/x86_64-linux-gnu/libnss_nisplus-2.15.so
/lib/x86_64-linux-gnu/libnss_files-2.15.so
/lib/x86_64-linux-gnu/libnss_nis-2.15.so
/lib/x86_64-linux-gnu/libcrypt-2.15.so
/lib/x86_64-linux-gnu/libnss_compat-2.15.so
/lib/x86_64-linux-gnu/libutil-2.15.so
/lib/x86_64-linux-gnu/libnss_hesiod-2.15.so
/lib/x86_64-linux-gnu/libnss_dns-2.15.so
/lib/x86_64-linux-gnu/libdl-2.15.so
/lib/x86_64-linux-gnu/libBrokenLocale-2.15.so
/lib/x86_64-linux-gnu/libSegFault.so
/lib/x86_64-linux-gnu/libanl-2.15.so
/lib/x86_64-linux-gnu/libpthread-2.15.so
/lib64
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libc6
/usr/share/doc/libc6/BUGS
/usr/share/doc/libc6/FAQ.gz
/usr/share/doc/libc6/test-results-x86_64-linux-gnu-libc
/usr/share/doc/libc6/README.hesiod.gz
/usr/share/doc/libc6/NEWS.gz
/usr/share/doc/libc6/copyright
/usr/share/doc/libc6/NEWS.Debian.gz
/usr/share/doc/libc6/README.Debian.gz
/usr/share/doc/libc6/changelog.Debian.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libc6
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libc
/usr/lib/x86_64-linux-gnu/libc/memcpy-syslog-preload.so
/usr/lib/x86_64-linux-gnu/libc/memcpy-preload.so
/usr/lib/x86_64-linux-gnu/gconv
/usr/lib/x86_64-linux-gnu/gconv/HP-ROMAN8.so
/usr/lib/x86_64-linux-gnu/gconv/KOI8-R.so
/usr/lib/x86_64-linux-gnu/gconv/IBM4517.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1149.so
/usr/lib/x86_64-linux-gnu/gconv/KOI8-RU.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1008_420.so
/usr/lib/x86_64-linux-gnu/gconv/gconv-modules
/usr/lib/x86_64-linux-gnu/gconv/CP737.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-11.so
/usr/lib/x86_64-linux-gnu/gconv/GEORGIAN-PS.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-8.so
/usr/lib/x86_64-linux-gnu/gconv/IBM870.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1025.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1167.so
/usr/lib/x86_64-linux-gnu/gconv/IBM5347.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-2.so
/usr/lib/x86_64-linux-gnu/gconv/EUC-KR.so
/usr/lib/x86_64-linux-gnu/gconv/IBM930.so
/usr/lib/x86_64-linux-gnu/gconv/KOI8-U.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-3.so
/usr/lib/x86_64-linux-gnu/gconv/IBM865.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1143.so
/usr/lib/x86_64-linux-gnu/gconv/UTF-32.so
/usr/lib/x86_64-linux-gnu/gconv/IBM866NAV.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-9E.so
/usr/lib/x86_64-linux-gnu/gconv/IBM857.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-6.so
/usr/lib/x86_64-linux-gnu/gconv/BIG5.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1161.so
/usr/lib/x86_64-linux-gnu/gconv/MIK.so
/usr/lib/x86_64-linux-gnu/gconv/EUC-JP-MS.so
/usr/lib/x86_64-linux-gnu/gconv/IBM9030.so
/usr/lib/x86_64-linux-gnu/gconv/IBM038.so
/usr/lib/x86_64-linux-gnu/gconv/EUC-TW.so
/usr/lib/x86_64-linux-gnu/gconv/CP1125.so
/usr/lib/x86_64-linux-gnu/gconv/MAC-IS.so
/usr/lib/x86_64-linux-gnu/gconv/ISO-2022-JP.so
/usr/lib/x86_64-linux-gnu/gconv/IBM935.so
/usr/lib/x86_64-linux-gnu/gconv/IBM9066.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1004.so
/usr/lib/x86_64-linux-gnu/gconv/CWI.so
/usr/lib/x86_64-linux-gnu/gconv/SJIS.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-AT-DE-A.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-ES-A.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-IT.so
/usr/lib/x86_64-linux-gnu/gconv/CP773.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1147.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1157.so
/usr/lib/x86_64-linux-gnu/gconv/INIS-CYRILLIC.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1162.so
/usr/lib/x86_64-linux-gnu/gconv/ISO-2022-CN-EXT.so
/usr/lib/x86_64-linux-gnu/gconv/IBM4909.so
/usr/lib/x86_64-linux-gnu/gconv/IBM902.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1097.so
/usr/lib/x86_64-linux-gnu/gconv/ISO-2022-JP-3.so
/usr/lib/x86_64-linux-gnu/gconv/IBM922.so
/usr/lib/x86_64-linux-gnu/gconv/IBM880.so
/usr/lib/x86_64-linux-gnu/gconv/ARMSCII-8.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_5427-EXT.so
/usr/lib/x86_64-linux-gnu/gconv/libJISX0213.so
/usr/lib/x86_64-linux-gnu/gconv/IBM903.so
/usr/lib/x86_64-linux-gnu/gconv/TIS-620.so
/usr/lib/x86_64-linux-gnu/gconv/GBBIG5.so
/usr/lib/x86_64-linux-gnu/gconv/IBM285.so
/usr/lib/x86_64-linux-gnu/gconv/HP-GREEK8.so
/usr/lib/x86_64-linux-gnu/gconv/ISO-IR-209.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1155.so
/usr/lib/x86_64-linux-gnu/gconv/TCVN5712-1.so
/usr/lib/x86_64-linux-gnu/gconv/MAC-UK.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-7.so
/usr/lib/x86_64-linux-gnu/gconv/LATIN-GREEK.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_2033.so
/usr/lib/x86_64-linux-gnu/gconv/IBM851.so
/usr/lib/x86_64-linux-gnu/gconv/IBM297.so
/usr/lib/x86_64-linux-gnu/gconv/IBM284.so
/usr/lib/x86_64-linux-gnu/gconv/KOI8-T.so
/usr/lib/x86_64-linux-gnu/gconv/IBM891.so
/usr/lib/x86_64-linux-gnu/gconv/DEC-MCS.so
/usr/lib/x86_64-linux-gnu/gconv/libKSC.so
/usr/lib/x86_64-linux-gnu/gconv/ISIRI-3342.so
/usr/lib/x86_64-linux-gnu/gconv/IBM437.so
/usr/lib/x86_64-linux-gnu/gconv/CP1256.so
/usr/lib/x86_64-linux-gnu/gconv/EUC-JISX0213.so
/usr/lib/x86_64-linux-gnu/gconv/IBM868.so
/usr/lib/x86_64-linux-gnu/gconv/IBM500.so
/usr/lib/x86_64-linux-gnu/gconv/CP775.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-FI-SE-A.so
/usr/lib/x86_64-linux-gnu/gconv/IBM420.so
/usr/lib/x86_64-linux-gnu/gconv/UTF-7.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1158.so
/usr/lib/x86_64-linux-gnu/gconv/IBM274.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1141.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1145.so
/usr/lib/x86_64-linux-gnu/gconv/IBM864.so
/usr/lib/x86_64-linux-gnu/gconv/CP10007.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_6937.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1112.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_11548-1.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-14.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1026.so
/usr/lib/x86_64-linux-gnu/gconv/ISO-IR-197.so
/usr/lib/x86_64-linux-gnu/gconv/CP1254.so
/usr/lib/x86_64-linux-gnu/gconv/libGB.so
/usr/lib/x86_64-linux-gnu/gconv/VISCII.so
/usr/lib/x86_64-linux-gnu/gconv/SHIFT_JISX0213.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1047.so
/usr/lib/x86_64-linux-gnu/gconv/BIG5HKSCS.so
/usr/lib/x86_64-linux-gnu/gconv/ISO-2022-KR.so
/usr/lib/x86_64-linux-gnu/gconv/CP774.so
/usr/lib/x86_64-linux-gnu/gconv/IBM933.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1129.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1137.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1399.so
/usr/lib/x86_64-linux-gnu/gconv/IBM273.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-DK-NO-A.so
/usr/lib/x86_64-linux-gnu/gconv/UHC.so
/usr/lib/x86_64-linux-gnu/gconv/IBM423.so
/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-15.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-DK-NO.so
/usr/lib/x86_64-linux-gnu/gconv/MAC-CENTRALEUROPE.so
/usr/lib/x86_64-linux-gnu/gconv/IBM863.so
/usr/lib/x86_64-linux-gnu/gconv/CP1258.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1132.so
/usr/lib/x86_64-linux-gnu/gconv/IBM290.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1046.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1154.so
/usr/lib/x86_64-linux-gnu/gconv/TSCII.so
/usr/lib/x86_64-linux-gnu/gconv/IBM256.so
/usr/lib/x86_64-linux-gnu/gconv/libJIS.so
/usr/lib/x86_64-linux-gnu/gconv/GREEK-CCITT.so
/usr/lib/x86_64-linux-gnu/gconv/IBM860.so
/usr/lib/x86_64-linux-gnu/gconv/CP770.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1124.so
/usr/lib/x86_64-linux-gnu/gconv/GREEK7.so
/usr/lib/x86_64-linux-gnu/gconv/CP1250.so
/usr/lib/x86_64-linux-gnu/gconv/LATIN-GREEK-1.so
/usr/lib/x86_64-linux-gnu/gconv/IBM9448.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-5.so
/usr/lib/x86_64-linux-gnu/gconv/EUC-JP.so
/usr/lib/x86_64-linux-gnu/gconv/ISO-2022-CN.so
/usr/lib/x86_64-linux-gnu/gconv/IBM856.so
/usr/lib/x86_64-linux-gnu/gconv/CP1252.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1133.so
/usr/lib/x86_64-linux-gnu/gconv/RK1048.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1390.so
/usr/lib/x86_64-linux-gnu/gconv/IBM901.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1164.so
/usr/lib/x86_64-linux-gnu/gconv/IBM871.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_6937-2.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_5428.so
/usr/lib/x86_64-linux-gnu/gconv/SAMI-WS2.so
/usr/lib/x86_64-linux-gnu/gconv/CP771.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-ES.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1388.so
/usr/lib/x86_64-linux-gnu/gconv/IBM904.so
/usr/lib/x86_64-linux-gnu/gconv/NATS-SEFI.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1146.so
/usr/lib/x86_64-linux-gnu/gconv/BRF.so
/usr/lib/x86_64-linux-gnu/gconv/IBM866.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-AT-DE.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1364.so
/usr/lib/x86_64-linux-gnu/gconv/HP-ROMAN9.so
/usr/lib/x86_64-linux-gnu/gconv/IBM852.so
/usr/lib/x86_64-linux-gnu/gconv/GBK.so
/usr/lib/x86_64-linux-gnu/gconv/HP-TURKISH8.so
/usr/lib/x86_64-linux-gnu/gconv/ANSI_X3.110.so
/usr/lib/x86_64-linux-gnu/gconv/ISO646.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-UK.so
/usr/lib/x86_64-linux-gnu/gconv/IBM921.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1371.so
/usr/lib/x86_64-linux-gnu/gconv/UNICODE.so
/usr/lib/x86_64-linux-gnu/gconv/ECMA-CYRILLIC.so
/usr/lib/x86_64-linux-gnu/gconv/IBM424.so
/usr/lib/x86_64-linux-gnu/gconv/JOHAB.so
/usr/lib/x86_64-linux-gnu/gconv/IBM861.so
/usr/lib/x86_64-linux-gnu/gconv/CP1257.so
/usr/lib/x86_64-linux-gnu/gconv/CP1253.so
/usr/lib/x86_64-linux-gnu/gconv/IBM918.so
/usr/lib/x86_64-linux-gnu/gconv/libCNS.so
/usr/lib/x86_64-linux-gnu/gconv/CSN_369103.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1142.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1008.so
/usr/lib/x86_64-linux-gnu/gconv/GEORGIAN-ACADEMY.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-13.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_5427.so
/usr/lib/x86_64-linux-gnu/gconv/IBM937.so
/usr/lib/x86_64-linux-gnu/gconv/IBM869.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-FI-SE.so
/usr/lib/x86_64-linux-gnu/gconv/IBM862.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1156.so
/usr/lib/x86_64-linux-gnu/gconv/IBM280.so
/usr/lib/x86_64-linux-gnu/gconv/IBM939.so
/usr/lib/x86_64-linux-gnu/gconv/IBM803.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-16.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-CA-FR.so
/usr/lib/x86_64-linux-gnu/gconv/MACINTOSH.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1144.so
/usr/lib/x86_64-linux-gnu/gconv/ASMO_449.so
/usr/lib/x86_64-linux-gnu/gconv/CP1251.so
/usr/lib/x86_64-linux-gnu/gconv/IEC_P27-1.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1122.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-1.so
/usr/lib/x86_64-linux-gnu/gconv/IBM277.so
/usr/lib/x86_64-linux-gnu/gconv/IBM4899.so
/usr/lib/x86_64-linux-gnu/gconv/NATS-DANO.so
/usr/lib/x86_64-linux-gnu/gconv/GOST_19768-74.so
/usr/lib/x86_64-linux-gnu/gconv/IBM16804.so
/usr/lib/x86_64-linux-gnu/gconv/HP-THAI8.so
/usr/lib/x86_64-linux-gnu/gconv/CP932.so
/usr/lib/x86_64-linux-gnu/gconv/IBM275.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1166.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-4.so
/usr/lib/x86_64-linux-gnu/gconv/PT154.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-US.so
/usr/lib/x86_64-linux-gnu/gconv/IBM905.so
/usr/lib/x86_64-linux-gnu/gconv/IBM12712.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-9.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-PT.so
/usr/lib/x86_64-linux-gnu/gconv/CP772.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1163.so
/usr/lib/x86_64-linux-gnu/gconv/UTF-16.so
/usr/lib/x86_64-linux-gnu/gconv/GREEK7-OLD.so
/usr/lib/x86_64-linux-gnu/gconv/KOI-8.so
/usr/lib/x86_64-linux-gnu/gconv/ISO8859-10.so
/usr/lib/x86_64-linux-gnu/gconv/IBM281.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-FR.so
/usr/lib/x86_64-linux-gnu/gconv/IBM875.so
/usr/lib/x86_64-linux-gnu/gconv/IBM4971.so
/usr/lib/x86_64-linux-gnu/gconv/GBGBK.so
/usr/lib/x86_64-linux-gnu/gconv/IBM874.so
/usr/lib/x86_64-linux-gnu/gconv/GB18030.so
/usr/lib/x86_64-linux-gnu/gconv/CP1255.so
/usr/lib/x86_64-linux-gnu/gconv/IBM850.so
/usr/lib/x86_64-linux-gnu/gconv/IBM855.so
/usr/lib/x86_64-linux-gnu/gconv/EUC-CN.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1153.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1160.so
/usr/lib/x86_64-linux-gnu/gconv/INIS-8.so
/usr/lib/x86_64-linux-gnu/gconv/T.61.so
/usr/lib/x86_64-linux-gnu/gconv/MAC-SAMI.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1140.so
/usr/lib/x86_64-linux-gnu/gconv/IBM278.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-IS-FRISS.so
/usr/lib/x86_64-linux-gnu/gconv/INIS.so
/usr/lib/x86_64-linux-gnu/gconv/libISOIR165.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1148.so
/usr/lib/x86_64-linux-gnu/gconv/EBCDIC-ES-S.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1130.so
/usr/lib/x86_64-linux-gnu/gconv/ISO_10367-BOX.so
/usr/lib/x86_64-linux-gnu/gconv/IBM943.so
/usr/lib/x86_64-linux-gnu/gconv/IBM1123.so
/usr/lib/x86_64-linux-gnu/gconv/IBM037.so
/usr/lib/x86_64-linux-gnu/gconv/IBM932.so
/lib/x86_64-linux-gnu/libnss_files.so.2
/lib/x86_64-linux-gnu/libnss_dns.so.2
/lib/x86_64-linux-gnu/libc.so.6
/lib/x86_64-linux-gnu/libdl.so.2
/lib/x86_64-linux-gnu/libnss_compat.so.2
/lib/x86_64-linux-gnu/libresolv.so.2
/lib/x86_64-linux-gnu/libnss_nis.so.2
/lib/x86_64-linux-gnu/libcidn.so.1
/lib/x86_64-linux-gnu/libcrypt.so.1
/lib/x86_64-linux-gnu/librt.so.1
/lib/x86_64-linux-gnu/libBrokenLocale.so.1
/lib/x86_64-linux-gnu/libthread_db.so.1
/lib/x86_64-linux-gnu/libnsl.so.1
/lib/x86_64-linux-gnu/libpthread.so.0
/lib/x86_64-linux-gnu/libanl.so.1
/lib/x86_64-linux-gnu/ld-linux-x86-64.so.2
/lib/x86_64-linux-gnu/libnss_hesiod.so.2
/lib/x86_64-linux-gnu/libm.so.6
/lib/x86_64-linux-gnu/libnss_nisplus.so.2
/lib/x86_64-linux-gnu/libutil.so.1
/lib64/ld-linux-x86-64.so.2
```/lib64/ld-linux-x86-64.so.2 is in there at the very end, so it does look like it was installed as part of that package.

> **matt_symes said:**
> Hi

It means that either the executable cannot be found or a dependant  dynamically loaded library. (ofcourse ther are other reasons for it as  well)

Maybe not the best error message in the world :smile:

Kind regards
Mhm, it could certainly do with being a bit more obvious for newbies like me who don't happen to know that :P

---

### Post by spjackson on 2012-07-24
> **matt_symes said:**
> 
Nice work [spjackson]("http://ubuntuforums.org/member.php?u=1128302"). Good call !!

Thank you for the appreciation. As I said, it was a bit of a guess - but a good one as it turns out. :-)

---

### Post by papibe on 2012-07-24
Try this:
```
sudo apt-get --reinstall install lib6c
```
Regards.

---

