---
title: "dovecot-2.0.5 on ubuntu 10.04 12.04 and 13.10 (i386/amd64)"
date: 2014-10-07
forum: Server Platforms
---

### Post by rmstock2 on 2014-10-07
Download is at  [http://www.crashrecovery.org/dovecot/](http://www.crashrecovery.org/dovecot/)  with the following braches (missing versions might show in due time) :

[http://www.crashrecovery.org/dovecot/ubuntu1004/amd64/](http://www.crashrecovery.org/dovecot/ubuntu1004/amd64/)
[http://www.crashrecovery.org/dovecot/ubuntu1204/i386/](http://www.crashrecovery.org/dovecot/ubuntu1204/i386/)
[http://www.crashrecovery.org/dovecot/ubuntu1310/amd64/](http://www.crashrecovery.org/dovecot/ubuntu1310/amd64/)
[http://www.crashrecovery.org/dovecot/ubuntu1310/i386/](http://www.crashrecovery.org/dovecot/ubuntu1310/i386/)


dovecot-2.0.5 on ubuntu 10.04 12.04 and 13.10 (i386/amd64)

 1. To install this you will need to have chkconfig installed. 
    For ubuntu 13.10 chkconfig_11.0-79.1-2_all.deb is available :

```
root@ubu1310:~# dpkg -i chkconfig_11.0-79.1-2_all.deb
Selecting previously unselected package chkconfig.
(Reading database ... 272226 files and directories currently installed.)
Unpacking chkconfig (from chkconfig_11.0-79.1-2_all.deb) ...
Setting up chkconfig (11.0-79.1-2) ...
Processing triggers for man-db ...
root@ubu1310:~# 
```

2. /sbin/insserv should exist, if not, create a symlink :
    
```
root@ubu1310:~# ln -s /usr/lib/insserv/insserv /sbin/insserv
root@ubu1310:~# ll /sbin/insserv 
lrwxrwxrwx 1 root root 24 okt  8 03:08 /sbin/insserv -> /usr/lib/insserv/insserv*
root@ubu1310:~#
```


 3. make sure /sbin/insserv does not come up with errors, besides
    its many warnings. A common error is a conflicting loop 
    between two or three `upstart' scripts. To resolve these 
    mostly loop errors use the tool : sysv-rc-conf :

```
root@ubu1310:~# apt-get install sysv-rc-conf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  id3v2 libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcurses-perl libcurses-ui-perl libterm-readkey-perl
The following NEW packages will be installed:
  libcurses-perl libcurses-ui-perl libterm-readkey-perl sysv-rc-conf
0 upgraded, 4 newly installed, 0 to remove and 156 not upgraded.
Need to get 388 kB of archives.
After this operation, 1271 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libcurses-perl amd64 1.28-1build2 [107 kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libterm-readkey-perl amd64 2.30-4build4 [28,4 kB]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libcurses-ui-perl all 0.9609-1 [229 kB]
Get:4 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe sysv-rc-conf all 0.99-7 [22,7 kB]
Fetched 388 kB in 0s (792 kB/s)    
Selecting previously unselected package libcurses-perl.
(Reading database ... 272799 files and directories currently installed.)
Unpacking libcurses-perl (from .../libcurses-perl_1.28-1build2_amd64.deb) ...
Selecting previously unselected package libterm-readkey-perl.
Unpacking libterm-readkey-perl (from .../libterm-readkey-perl_2.30-4build4_amd64.deb) ...
Selecting previously unselected package libcurses-ui-perl.
Unpacking libcurses-ui-perl (from .../libcurses-ui-perl_0.9609-1_all.deb) ...
Selecting previously unselected package sysv-rc-conf.
Unpacking sysv-rc-conf (from .../sysv-rc-conf_0.99-7_all.deb) ...
Processing triggers for man-db ...
Setting up libcurses-perl (1.28-1build2) ...
Setting up libterm-readkey-perl (2.30-4build4) ...
Setting up libcurses-ui-perl (0.9609-1) ...
Setting up sysv-rc-conf (0.99-7) ...
root@ubu1310:~# 
```

 4. make sure that insserv does not report any errors, by checking with
    /sbin/insserv and adjusting with sysv-rc-conf (/usr/sbin/sysv-rc-conf).

 5. install dovecot as follows :

```
 root@ubu1310:~# dpkg -i dovecot-common_2.0.5-1ubuntu1_amd64.deb 
Selecting previously unselected package dovecot-common.
(Reading database ... 272231 files and directories currently installed.)
Unpacking dovecot-common (from dovecot-common_2.0.5-1ubuntu1_amd64.deb) ...
Setting up dovecot-common (1:2.0.5-1ubuntu1) ...
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
dovecot                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
Processing triggers for ureadahead ...
Info: Generating SSL parameters
Generating a 1024 bit RSA private key
..Processing triggers for man-db ...
............++++++
...................++++++
writing new private key to '/etc/pki/dovecot/private/dovecot.pem'
-----

subject= /OU=IMAP server/CN=imap.example.com/emailAddress=postmaster@example.com
SHA1 Fingerprint=6E:97:68:9F:70:F4:E3:8F:77:E3:49:E6:FE:4B:BD:55:93:8C:79:EB
root@ubu1310:~# Info: SSL parameters regeneration completed
root@ubu1310:~# 
```

6. Startup your dovecot :

```
root@ubu1310:~# service dovecot status
 * Dovecot is not running
root@ubu1310:~# service dovecot start
 * Starting Dovecot Imap: dovecot  
Warning: Corrected permissions for login directory /var/run/dovecot/login
                                                                         [ OK ]
root@ubu1310:~# service dovecot status
 * Dovecot is running
root@ubu1310:~#
root@ubu1310:~#
root@ubu1310:~# doveconf -n
# 2.0.5: /etc/dovecot/dovecot.conf
# OS: Linux 3.11.0-18-generic x86_64 Ubuntu 13.10 
debug_log_path = /var/log/dovecot/debug
info_log_path = /var/log/dovecot/info
log_path = /var/log/dovecot/error
mbox_write_locks = fcntl
passdb {
  driver = pam
}
ssl_cert = <//etc/pki/dovecot/certs/dovecot.pem
ssl_key = <//etc/pki/dovecot/private/dovecot.pem
userdb {
  driver = passwd
}
root@ubu1310:~#
root@ubu1310:~# dovecot --version
2.0.5
root@ubu1310:~# dovecot --build-options
Build options: ioloop=epoll notify=inotify ipv6 openssl io_block_size=8192
Mail storages: cydir maildir mbox mdbox raw sdbox shared
SQL driver plugins: mysql postgresql sqlite
Passdb: checkpassword ldap pam passwd passwd-file shadow sql
Userdb: checkpassword ldap(plugin) nss passwd prefetch passwd-file sql
root@ubu1310:~# 
root@ubu1310:~# cd /usr/lib/dovecot/
root@ubu1310:/usr/lib/dovecot# ll
total 11328
drwxr-xr-x   3 root root    4096 okt  8 04:03 ./
drwxr-xr-x 167 root root   20480 okt  8 04:03 ../
-rwxr-xr-x   1 root root   60952 okt  8 00:00 anvil*
-rwxr-xr-x   1 root root 1167170 okt  8 00:00 auth*
-rwxr-xr-x   1 root root   18039 okt  8 00:00 checkpassword-reply*
-rwxr-xr-x   1 root root  280140 okt  8 00:00 config*
lrwxrwxrwx   1 root root      11 okt  8 00:00 deliver -> dovecot-lda*
-rwxr-xr-x   1 root root  223312 okt  8 00:00 dict*
-rwxr-xr-x   1 root root  220907 okt  8 00:00 director*
-rwxr-xr-x   1 root root   26130 okt  8 00:00 dns-client*
-rwxr-xr-x   1 root root  275316 okt  8 00:00 doveadm-server*
-rw-r--r--   1 root root    2346 okt  7 23:58 dovecot-config
-rwxr-xr-x   1 root root   77049 okt  8 00:00 dovecot-lda*
-rwxr-xr-x   1 root root   19129 okt  8 00:00 gdbhelper*
-rwxr-xr-x   1 root root  790580 okt  8 00:00 imap*
-rwxr-xr-x   1 root root   80690 okt  8 00:00 imap-login*
lrwxrwxrwx   1 root root      23 okt  8 00:00 libdovecot-lda.so -> libdovecot-lda.so.0.0.0
lrwxrwxrwx   1 root root      23 okt  8 00:00 libdovecot-lda.so.0 -> libdovecot-lda.so.0.0.0
-rw-r--r--   1 root root  138560 okt  8 00:00 libdovecot-lda.so.0.0.0
lrwxrwxrwx   1 root root      25 okt  8 00:00 libdovecot-login.so -> libdovecot-login.so.0.0.0
lrwxrwxrwx   1 root root      25 okt  8 00:00 libdovecot-login.so.0 -> libdovecot-login.so.0.0.0
-rw-r--r--   1 root root  308025 okt  8 00:00 libdovecot-login.so.0.0.0
lrwxrwxrwx   1 root root      19 okt  8 00:00 libdovecot.so -> libdovecot.so.0.0.0
lrwxrwxrwx   1 root root      19 okt  8 00:00 libdovecot.so.0 -> libdovecot.so.0.0.0
-rw-r--r--   1 root root 1995769 okt  8 00:00 libdovecot.so.0.0.0
lrwxrwxrwx   1 root root      27 okt  8 00:00 libdovecot-storage.so -> libdovecot-storage.so.0.0.0
lrwxrwxrwx   1 root root      27 okt  8 00:00 libdovecot-storage.so.0 -> libdovecot-storage.so.0.0.0
-rw-r--r--   1 root root 5182236 okt  8 00:00 libdovecot-storage.so.0.0.0
-rwxr-xr-x   1 root root   24878 okt  8 00:00 listview*
-rwxr-xr-x   1 root root  175806 okt  8 00:00 lmtp*
-rwxr-xr-x   1 root root   43201 okt  8 00:00 log*
-rwxr-xr-x   1 root root   23087 okt  8 00:00 maildirlock*
-rwxr-xr-x   1 root root     931 okt  7 23:58 mkcert.sh*
drwxr-xr-x   5 root root    4096 okt  8 04:03 modules/
-rwxr-xr-x   1 root root  132339 okt  8 00:00 pop3*
-rwxr-xr-x   1 root root   64582 okt  8 00:00 pop3-login*
-rwxr-xr-x   1 root root   39359 okt  8 00:00 rawlog*
-rwxr-xr-x   1 root root   25438 okt  8 00:00 script*
-rwxr-xr-x   1 root root   33949 okt  8 00:00 script-login*
-rwxr-xr-x   1 root root   54791 okt  8 00:00 ssl-params*
-rwxr-xr-x   1 root root   26093 okt  8 00:00 tcpwrap*
root@ubu1310:/usr/lib/dovecot# 
root@ubu1310:/usr/lib/dovecot# cd /var/run/dovecot/
root@ubu1310:/var/run/dovecot# ll
total 4
drwxr-xr-x  4 root    root     420 okt  8 04:03 ./
drwxr-xr-x 22 root    root     780 okt  8 04:03 ../
srw-------  1 root    root       0 okt  8 04:03 anvil=
srw-------  1 root    root       0 okt  8 04:03 anvil-auth-penalty=
srw-------  1 root    root       0 okt  8 04:03 auth-client=
srw-------  1 dovecot root       0 okt  8 04:03 auth-login=
srw-------  1 root    root       0 okt  8 04:03 auth-master=
srw-------  1 root    root       0 okt  8 04:03 auth-userdb=
srw-------  1 dovecot root       0 okt  8 04:03 auth-worker=
srw-------  1 root    root       0 okt  8 04:03 config=
srw-------  1 root    root       0 okt  8 04:03 dict=
srw-------  1 root    root       0 okt  8 04:03 director-admin=
srw-------  1 root    root       0 okt  8 04:03 director-userdb=
srw-rw-rw-  1 root    root       0 okt  8 04:03 dns-client=
srw-------  1 root    root       0 okt  8 04:03 doveadm-server=
lrwxrwxrwx  1 root    root      25 okt  8 04:03 dovecot.conf -> /etc/dovecot/dovecot.conf
-rw-r--r--  1 root    root       0 okt  8 04:03 dovecot.lock
drwxr-xr-x  2 root    root      40 okt  8 00:00 empty/
srw-rw-rw-  1 root    root       0 okt  8 04:03 lmtp=
drwxr-x---  2 root    dovenull 140 okt  8 04:03 login/
-rw-------  1 root    root       5 okt  8 04:03 master.pid
root@ubu1310:/var/run/dovecot#

```

 7. To remove dovecot it has to be running to remove it properly :

```
root@ubu1310:~# service dovecot status
 * Dovecot is running
root@ubu1310:~# dpkg --purge dovecot-common
(Reading database ... 272932 files and directories currently installed.)
Removing dovecot-common ...
insserv: warning: script 'console-setup' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-setup'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-setup'
insserv: warning: script 'setvtrgb' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `setvtrgb'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `setvtrgb'
insserv: warning: script 'rfkill-store' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-store'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-store'
insserv: warning: script 'kmod' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `kmod'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `kmod'
insserv: warning: script 'rfkill-restore' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `rfkill-restore'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `rfkill-restore'
insserv: warning: script 'resolvconf' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `resolvconf'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `resolvconf'
insserv: warning: script 'cron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `cron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `cron'
insserv: warning: script 'console-font' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `console-font'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `console-font'
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `atd'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `atd'
insserv: warning: script 'anacron' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `anacron'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `anacron'
insserv: warning: script 'friendly-recovery' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `friendly-recovery'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `friendly-recovery'
insserv: warning: script 'bluetooth' missing LSB tags and overrides
insserv: Default-Start undefined, assuming empty start runlevel(s) for script `bluetooth'
insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `bluetooth'
dovecot                   0:off  1:off  2:off  3:off  4:off  5:off  6:off
Purging configuration files for dovecot-common ...
dpkg: warning: while removing dovecot-common, directory '/var/lib/dovecot' not empty so not removed
dpkg: warning: while removing dovecot-common, directory '/var/log/dovecot' not empty so not removed
Processing triggers for man-db ...
Processing triggers for ureadahead ...
root@ubu1310:~# dpkg -l dovecot-common
dpkg-query: no packages found matching dovecot-common
root@ubu1310:~# 

```

---

