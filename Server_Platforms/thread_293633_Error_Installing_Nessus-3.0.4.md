---
title: "Error Installing Nessus-3.0.4"
date: 2006-11-05
forum: Server Platforms
---

### Post by drlamer on 2006-11-05
hey sup?

i`m using Ubuntu 6.10 Edgy Eft

i download Nessus 3.0.4, when i`m trying to install with- 
"dpkg -i Nessus-3.0.4-debian3_i386.deb" i`m getting the following error

dpkg -i Nessus-3.0.4-debian3_i386.deb
Selecting previously deselected package nessus.
(Reading database ... 92051 files and directories currently installed.)
Unpacking nessus (from Nessus-3.0.4-debian3_i386.deb) ...
Setting up nessus (3.0.4) ...
/var/lib/dpkg/info/nessus.postinst: 6: Syntax error: redirection unexpected
dpkg: error processing nessus (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 nessus

any workaround? OR fix?
tnx

---

### Post by zuchuat on 2006-11-07
Hello,

I have solved this by editing the /var/lib/dpkg/info/nessus.postinst script and changing the header (#!/bin/sh) by #!/bin/bash, and manualy reexecuting the script.

Before, think to make symbol links for libssl and libcrypto, this is explained in another post : [http://www.ubuntuforums.org/showthread.php?t=223782&highlight=nessus](http://www.ubuntuforums.org/showthread.php?t=223782&highlight=nessus)

# cd /usr/lib
# ln -s libcrypto.so.0.9.8 libcrypto.so.0.9.7
# ln -s libssl.so.0.9.8 libssl.so.0.9.


Good luck.
Bye

---

### Post by drlamer on 2006-11-08
did not work 4 me :-(

still getting error

tnx 4 your reply

---

### Post by pr4vst3r on 2006-11-14
Relink /bin/sh to /bin/bash (Linked to /bin/dash by default):

as root:
rm /bin/sh
ln -s /bin/bash /bin/sh

Follow the re-linking of crypto and ssl as per previous post

---

### Post by ulrick on 2006-11-21
Thanks pr4vst3r,

This last solution worked for me ...
The symbol links for libssl and libcrypto were already there before (when i wanted to create them, he stated that they were already there).

Thanks a lot
Now, (K)ubuntu is again supported :D

---

### Post by tylerdurden on 2006-11-27
hey all:

i am having the same problems... i edited the file to reflect bash instead of sh and i created the symbolic links... u said to manually run the script again... do i need to chmod +x nessus.postinst? is that the file i manually run... when i do ./nessus.postinst, nothing happens after i chmod +x it... any help is GREATLY appreciated...

---

### Post by Bjoeboo on 2006-12-19
> **zuchuat said:**
> Hello,

I have solved this by editing the /var/lib/dpkg/info/nessus.postinst script and changing the header (#!/bin/sh) by #!/bin/bash, and manualy reexecuting the script.

Before, think to make symbol links for libssl and libcrypto, this is explained in another post : [http://www.ubuntuforums.org/showthread.php?t=223782&highlight=nessus](http://www.ubuntuforums.org/showthread.php?t=223782&highlight=nessus)

# cd /usr/lib
# ln -s libcrypto.so.0.9.8 libcrypto.so.0.9.7
# ln -s libssl.so.0.9.8 libssl.so.0.9.


Good luck.
Bye

I believe SHOULD read:
# cd /usr/lib
# ln -s libcrypto.so.0.9.8 libcrypto.so.0.9.7
# ln -s libssl.so.0.9.8 libssl.so.0.9.7

left off the last 7
install seems to be progressing nicely now...

---

### Post by shahin on 2007-03-10
I can not get rid of this error:

nessusd: error while loading shared libraries: libnessus.so.3: cannot open shared object file: No such file or directory

Is this similar to the ssl error?  Why does this happen please?  How does making symbolic link fix the issue please?

---

### Post by shahin on 2007-03-10
Ok I was able to get rid of the previous error by using the advice over here:
[http://forums.remote-exploit.org/showthread.php?t=462&page=2](http://forums.remote-exploit.org/showthread.php?t=462&page=2)

but the commands you mentioned for ssl library does not fix my *new* problem with ssl:

rm /bin/sh
ln -s /bin/bash /bin/sh
ln -s libssl.so.0.9.8 libssl.so.0.9.7
ln: accessing `libssl.so.0.9.7': Too many levels of symbolic links  // not sure what this means
ln -s libcrypto.so.0.9.8 libcrypto.so.0.9.7

 /opt/nessus/bin/nessus-fetch --register *************************
/opt/nessus/bin/nessus-fetch: error while loading shared libraries: libssl.so.0.9.7: cannot open shared object file: No such file or directory

---

### Post by shahin on 2007-03-10
Ok between the url I posted earlier, and the commands you mentioned, things worked out and I am now running nessus:-) thank you all.

---

