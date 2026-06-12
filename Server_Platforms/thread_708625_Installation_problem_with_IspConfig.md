---
title: "Installation problem with IspConfig"
date: 2008-02-26
forum: Server Platforms
---

### Post by wulfer on 2008-02-26
I keep getting the same error on installing IspConfig on my Gutsy Gibbon machine.
[B]ERROR: The PHP binary coming with ISPConfig does not work properly on your system! The installation routine stops here!
[/B]

Complete error log on ./configure:
> ./configure:Error: APACI failed
ERROR: Could not configure Apache
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
./setup2: line 873: ispconfig_tmp/php/bin/php: No such file or directory
ERROR: The PHP binary coming with ISPConfig does not work properly on your system! The installation routine stops here!

I tried to solve it by installing the mysql-devel, but couldn't find it. I read on several forums it could be replaced with libmysqlclient15,
but after installing that, I still have the same error.

Any help is highly appreciated!

---

### Post by teebone on 2008-04-27
I realize that this thread is somewhat old, but if you still wonder, and perhaps it will help others with the same problem, what solved it for me was installing the libmysql++-dev package :)

sudo aptitude install libmysql++-dev <- should do the trick. I hope  :)

---

