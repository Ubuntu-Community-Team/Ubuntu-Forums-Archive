---
title: "ISPConfig installation issue."
date: 2007-07-15
forum: Server Platforms
---

### Post by RickR on 2007-07-15
Hi. I'm pretty new to server installation and such, and I've been following the guide here: [http://www.howtoforge.com/perfect_setup_ubuntu704](http://www.howtoforge.com/perfect_setup_ubuntu704). I think I got everything done. I'm now installing ISPConfig. It gave me an error and quit, and I can't seem to find help elsewhere.

Here's the section that started to go wrong...
> Verify failure
unable to write key
29572:error:0906406D:PEM routines:PEM_def_callback:problems getting password:pem_lib.c:105:
29572:error:0906906F:PEM routines:PEM_ASN1_write_bio:read key:pem_lib.c:331:
mkcert.sh:Error: Failed to encrypt RSA private key
make[1]: *** [certificate] Error 1
make[1]: Leaving directory `/home/rick/install_ispconfig/compile_aps/apache_1.3.37/src'
make: *** [certificate] Error 2
ERROR: Could not make certificate for Apache
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


Any ideas what went wrong? Thanks in advance.

---

### Post by erito on 2007-07-29
Hi RickR
Not sure if your still having the same problem, but try linking your /bin/sh to /bin/dash as shown at the bottom of this page:
[http://www.howtoforge.com/perfect_setup_ubuntu704_p3?](http://www.howtoforge.com/perfect_setup_ubuntu704_p3?)
I was having the exact same problem and it worked for me.  Hope that works.

erito

---

### Post by dysolve on 2007-09-24
I am having the same issue, but my bin/bash is good.. everything else worked fine.. any ideas? I will post error to here after I try again!

---

