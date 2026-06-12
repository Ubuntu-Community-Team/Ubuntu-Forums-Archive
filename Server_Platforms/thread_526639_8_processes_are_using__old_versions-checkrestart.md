---
title: "8 processes are using  old versions-checkrestart"
date: 2007-08-15
forum: Server Platforms
---

### Post by joepie on 2007-08-15
#checkrestart
Found 8 processes using old versions of upgraded files
(3 distinct programs)
(3 distinct packages)

Of these, 0 seem to contain init scripts which can be used to restart them:


Here are the others:
firefox:
        22687   /usr/lib/firefox/firefox-bin
upstart:
        1       /sbin/init
apache2-mpm-prefork:
        5680    /usr/sbin/apache2
        5682    /usr/sbin/apache2
        5674    /usr/sbin/apache2

on a fresh 7.04 server + 7.04 desktop+webmin install.
my ubuntu system got hacked, so this new system shouldn't run old versions.

How can i force it to use the right version ?

Cheers

pivotter


        5676    /usr/sbin/apache2
        5675    /usr/sbin/apache2
        5679    /usr/sbin/apache2

---

### Post by a9k on 2007-08-17
I suspect that checkrestart is not giving useful information in this case. I'm running Gutsy and get the same error on apache2-mpm-worker.

If you were hacked, my heart goes out to you. I found I had to make a new server then wipe the old one. There were just too many things corrupted, including the kernel, grub, and most of the major command line tools.

Good Luck.

---

