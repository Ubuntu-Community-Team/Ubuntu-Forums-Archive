---
title: "Install Issue IspConfig vs openssl"
date: 2009-09-27
forum: Server Platforms
---

### Post by ruralbb.com on 2009-09-27
I am attempting to install ispconfig2 and get the following info on the error...

cc1: error: unrecognized command line option "-m486"
make[1]: *** [cryptlib.o] Error 1
make[1]: Leaving directory `/home/******/install_ispconfig/compile_aps/openssl-0.9.7m/crypto'
make: *** [sub_all] Error 1
ERROR: Could not make OpenSSL
cd: error retrieving current directory: getcwd: cannot access parent directories: No such file or directory
mv: cannot stat `binaries/aps.tar.gz': No such file or directory
mv: cannot stat `binaries/spamassassin.tar.gz': No such file or directory
mv: cannot stat `binaries/uudeview.tar.gz': No such file or directory
mv: cannot stat `binaries/clamav.tar.gz': No such file or directory
mv: cannot stat `binaries/cronolog': No such file or directory
mv: cannot stat `binaries/cronosplit': No such file or directory
mv: cannot stat `binaries/ispconfig_tcpserver': No such file or directory
mv: cannot stat `binaries/zip': No such file or directory
mv: cannot stat `binaries/unzip': No such file or directory
tar: spamassassin.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `spamassassin': No such file or directory
tar: uudeview.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `uudeview': No such file or directory
tar: clamav.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mv: cannot stat `clamav': No such file or directory
tar: aps.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
./setup2: line 888: ispconfig_tmp/php/bin/php: No such file or directory
ERROR: The PHP binary coming with ISPConfig does not work properly on your system! The installation routine stops here!

I am not an expert on this os but it looks to me I am missing some files...as far as the openssl I have a newer version.  Is this the issue?

can anyone help me follow the correct path...

Thanks in advance...

Rob

I found this solution but I dont understand what I am suppose to do...

[I][COLOR="Red"]Workaround to get it to work on debian lenny:


Go to compile_apps , unpack openssl-0.9.7m.tar.gz
edit Configure and Makefile and change all instances of -m486 to -mtune=i486 .

Run
"tar -pczf openssl-0.9.7m.tar.gz openssl-0.9.7m" to repack dir, remove the unpacked directory.


Make sure you do this before running ./setup on any upgrades in the future until this is fixed in ./setup package.[/COLOR][/I]

---

### Post by ruralbb.com on 2009-09-29
I scrapped the ispconfig2 and used ispconfig3

Thanks for nothing...

---

