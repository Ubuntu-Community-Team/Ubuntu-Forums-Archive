---
title: "Error when logging in via SSH"
date: 2012-10-04
forum: Server Platforms
---

### Post by CAIS on 2012-10-04
I have a rackspace cloud server running ubuntu 10.04. When I try to connect to the server via SSH I get the password prompt. After entering the password I get a long error message (pasted below) and then the connection is closed. Please let me know if you have any ideas on how to fix this. Thanks!

-----------------------
```
*** invalid open call: O_CREAT without mode ***: sshd: root@pts/0 terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7faf3dd007e7]
/lib/libc.so.6(+0xdda31)[0x7faf3dcdea31]
sshd: root@pts/0[0x41b1e2]
sshd: root@pts/0[0x41b908]
sshd: root@pts/0[0x41ba20]
sshd: root@pts/0[0x409e10]
sshd: root@pts/0[0x412215]
sshd: root@pts/0[0x41242b]
sshd: root@pts/0[0x412564]
sshd: root@pts/0[0x412867]
sshd: root@pts/0[0x40bc83]
sshd: root@pts/0[0x42ccce]
sshd: root@pts/0[0x40cc56]
sshd: root@pts/0[0x412ae3]
sshd: root@pts/0[0x4071d8]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7faf3dc1fc4d]
sshd: root@pts/0[0x405a39]
======= Memory map: ========
00400000-00447000 r-xp 00000000 ca:01 3245351                            /usr/sbin/sshd
00646000-00647000 r--p 00046000 ca:01 3245351                            /usr/sbin/sshd
00647000-00648000 rw-p 00047000 ca:01 3245351                            /usr/sbin/sshd
00648000-0074f000 rw-p 00000000 00:00 0 
00cb8000-00cd9000 rw-p 00000000 00:00 0                                  [heap]
7faf3cc66000-7faf3cc7c000 r-xp 00000000 ca:01 4849733                    /lib/libgcc_s.so.1
7faf3cc7c000-7faf3ce7b000 ---p 00016000 ca:01 4849733                    /lib/libgcc_s.so.1
7faf3ce7b000-7faf3ce7c000 r--p 00015000 ca:01 4849733                    /lib/libgcc_s.so.1
7faf3ce7c000-7faf3ce7d000 rw-p 00016000 ca:01 4849733                    /lib/libgcc_s.so.1
7faf3ce7d000-7faf3ce93000 r-xp 00000000 ca:01 4850287                    /lib/libresolv-2.11.1.so
7faf3ce93000-7faf3d092000 ---p 00016000 ca:01 4850287                    /lib/libresolv-2.11.1.so
7faf3d092000-7faf3d093000 r--p 00015000 ca:01 4850287                    /lib/libresolv-2.11.1.so
7faf3d093000-7faf3d094000 rw-p 00016000 ca:01 4850287                    /lib/libresolv-2.11.1.so
7faf3d094000-7faf3d096000 rw-p 00000000 00:00 0 
7faf3d096000-7faf3d09b000 r-xp 00000000 ca:01 4850302                    /lib/libnss_dns-2.11.1.so
7faf3d09b000-7faf3d29a000 ---p 00005000 ca:01 4850302                    /lib/libnss_dns-2.11.1.so
7faf3d29a000-7faf3d29b000 r--p 00004000 ca:01 4850302                    /lib/libnss_dns-2.11.1.so
7faf3d29b000-7faf3d29c000 rw-p 00005000 ca:01 4850302                    /lib/libnss_dns-2.11.1.so
7faf3d29c000-7faf3d3dc000 rw-s 00000000 00:04 1704224                    /dev/zero (deleted)
7faf3d3dc000-7faf3d3e8000 r-xp 00000000 ca:01 4850306                    /lib/libnss_files-2.11.1.so
7faf3d3e8000-7faf3d5e7000 ---p 0000c000 ca:01 4850306                    /lib/libnss_files-2.11.1.so
7faf3d5e7000-7faf3d5e8000 r--p 0000b000 ca:01 4850306                    /lib/libnss_files-2.11.1.so
7faf3d5e8000-7faf3d5e9000 rw-p 0000c000 ca:01 4850306                    /lib/libnss_files-2.11.1.so
7faf3d5e9000-7faf3d5f3000 r-xp 00000000 ca:01 4850291                    /lib/libnss_nis-2.11.1.so
7faf3d5f3000-7faf3d7f2000 ---p 0000a000 ca:01 4850291                    /lib/libnss_nis-2.11.1.so
7faf3d7f2000-7faf3d7f3000 r--p 00009000 ca:01 4850291                    /lib/libnss_nis-2.11.1.so
7faf3d7f3000-7faf3d7f4000 rw-p 0000a000 ca:01 4850291                    /lib/libnss_nis-2.11.1.so
7faf3d7f4000-7faf3d7fc000 r-xp 00000000 ca:01 4850290                    /lib/libnss_compat-2.11.1.so
7faf3d7fc000-7faf3d9fb000 ---p 00008000 ca:01 4850290                    /lib/libnss_compat-2.11.1.so
7faf3d9fb000-7faf3d9fc000 r--p 00007000 ca:01 4850290                    /lib/libnss_compat-2.11.1.so
7faf3d9fc000-7faf3d9fd000 rw-p 00008000 ca:01 4850290                    /lib/libnss_compat-2.11.1.so
7faf3d9fd000-7faf3d9ff000 r-xp 00000000 ca:01 4850307                    /lib/libdl-2.11.1.so
7faf3d9ff000-7faf3dbff000 ---p 00002000 ca:01 4850307                    /lib/libdl-2.11.1.so
7faf3dbff000-7faf3dc00000 r--p 00002000 ca:01 4850307                    /lib/libdl-2.11.1.so
7faf3dc00000-7faf3dc01000 rw-p 00003000 ca:01 4850307                    /lib/libdl-2.11.1.so
7faf3dc01000-7faf3dd7b000 r-xp 00000000 ca:01 4850303                    /lib/libc-2.11.1.so
7faf3dd7b000-7faf3df7a000 ---p 0017a000 ca:01 4850303                    /lib/libc-2.11.1.so
7faf3df7a000-7faf3df7e000 r--p 00179000 ca:01 4850303                    /lib/libc-2.11.1.so
7faf3df7e000-7faf3df7f000 rw-p 0017d000 ca:01 4850303                    /lib/libc-2.11.1.so
7faf3df7f000-7faf3df84000 rw-p 00000000 00:00 0 
7faf3df84000-7faf3df8d000 r-xp 00000000 ca:01 4850284                    /lib/libcrypt-2.11.1.so
7faf3df8d000-7faf3e18d000 ---p 00009000 ca:01 4850284                    /lib/libcrypt-2.11.1.so
7faf3e18d000-7faf3e18e000 r--p 00009000 ca:01 4850284                    /lib/libcrypt-2.11.1.so
7faf3e18e000-7faf3e18f000 rw-p 0000a000 ca:01 4850284                    /lib/libcrypt-2.11.1.so
7faf3e18f000-7faf3e1bd000 rw-p 00000000 00:00 0 
7faf3e1bd000-7faf3e325000 r-xp 00000000 ca:01 4849853                    /lib/libcrypto.so.0.9.8
7faf3e325000-7faf3e525000 ---p 00168000 ca:01 4849853                    /lib/libcrypto.so.0.9.8
7faf3e525000-7faf3e532000 r--p 00168000 ca:01 4849853                    /lib/libcrypto.so.0.9.8
7faf3e532000-7faf3e54a000 rw-p 00175000 ca:01 4849853                    /lib/libcrypto.so.0.9.8
7faf3e54a000-7faf3e54e000 rw-p 00000000 00:00 0 
7faf3e54e000-7faf3e565000 r-xp 00000000 ca:01 4850280                    /lib/libnsl-2.11.1.so
7faf3e565000-7faf3e764000 ---p 00017000 ca:01 4850280                    /lib/libnsl-2.11.1.so
7faf3e764000-7faf3e765000 r--p 00016000 ca:01 4850280                    /lib/libnsl-2.11.1.so
7faf3e765000-7faf3e766000 rw-p 00017000 ca:01 4850280                    /lib/libnsl-2.11.1.so
7faf3e766000-7faf3e768000 rw-p 00000000 00:00 0 
7faf3e768000-7faf3e77e000 r-xp 00000000 ca:01 4849923                    /lib/libz.so.1.2.3.3
7faf3e77e000-7faf3e97d000 ---p 00016000 ca:01 4849923                    /lib/libz.so.1.2.3.3
7faf3e97d000-7faf3e97e000 r--p 00015000 ca:01 4849923                    /lib/libz.so.1.2.3.3
7faf3e97e000-7faf3e97f000 rw-p 00016000 ca:01 4849923                    /lib/libz.so.1.2.3.3
7faf3e97f000-7faf3e981000 r-xp 00000000 ca:01 4850295                    /lib/libutil-2.11.1.so
7faf3e981000-7faf3eb80000 ---p 00002000 ca:01 4850295                    /lib/libutil-2.11.1.so
7faf3eb80000-7faf3eb81000 r--p 00001000 ca:01 4850295                    /lib/libutil-2.11.1.so
7faf3eb81000-7faf3eb82000 rw-p 00002000 ca:01 4850295                    /lib/libutil-2.11.1.soConnection to [www.cais.org](www.cais.org) closed.
```

---

### Post by CAIS on 2012-10-04
In case anybody else runs into this--I managed to fix this by reinstalling ssh server:

sudo apt-get --reinstall install openssh-server

But first I had to change some attributes by following instructions here:

[http://www.howtoforge.com/debian-ubuntu-unable-to-make-backup-link-of-usr-bin-sshd-before-installing-new-version-operation-not-permitted](http://www.howtoforge.com/debian-ubuntu-unable-to-make-backup-link-of-usr-bin-sshd-before-installing-new-version-operation-not-permitted)

---

### Post by yzhou88 on 2013-03-11
Thank you! Your idea works.
You saved my server!

> **CAIS said:**
> In case anybody else runs into this--I managed to fix this by reinstalling ssh server:

sudo apt-get --reinstall install openssh-server

But first I had to change some attributes by following instructions here:

[http://www.howtoforge.com/debian-ubuntu-unable-to-make-backup-link-of-usr-bin-sshd-before-installing-new-version-operation-not-permitted](http://www.howtoforge.com/debian-ubuntu-unable-to-make-backup-link-of-usr-bin-sshd-before-installing-new-version-operation-not-permitted)

---

