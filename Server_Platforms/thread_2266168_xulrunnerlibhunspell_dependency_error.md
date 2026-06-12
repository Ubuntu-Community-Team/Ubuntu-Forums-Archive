---
title: "xulrunner/libhunspell dependency error"
date: 2015-02-20
forum: Server Platforms
---

### Post by jmaciak1987 on 2015-02-20
After upgrading from 10.04 to 12.04 to 14.04, I have an unmet dependency when doing an apt-get upgrade:
```
root@server:/home# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 xulrunner-1.9.2 : Depends: libhunspell-1.2-0 (>= 1.2.8) but it is not installable
E: Unmet dependencies. Try using -f.
```

Ok, well I tried apt-get -f install of course...

```
root@server:/home# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gwibber-service python-avahi python-couchdb
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xulrunner-1.9.2
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 30.9 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 732159 files and directories currently installed.)
Removing xulrunner-1.9.2 (1.9.2.28+build1+nobinonly-0ubuntu0.10.04.1) ...
/var/lib/dpkg/info/xulrunner-1.9.2.prerm: 8: /var/lib/dpkg/info/xulrunner-1.9.2.prerm: /usr/sbin/update-alternatives: not found
dpkg: error processing package xulrunner-1.9.2 (--remove):
 subprocess installed pre-removal script returned error exit status 127
/usr/lib/xulrunner-1.9.2.28/xulrunner-bin: error while loading shared libraries: libhunspell-1.2.so.0: cannot open shared object file: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

No dice. Can't remove or purge either xulrunner or libhunspell. Tried cleaning the apt cache as well. I don't need either package, so I rather just nuke them. Thoughts?

Searched and couldn't find an exact answer...

---

### Post by chris_davis3 on 2015-02-20
Hi, I just booted up an old hardy heron box and upgraded it to the most recent ubuntu and I'm getting this error and i've tried everything online to fix it with no luck is there anything else one can do to fix this? Thanks



ad-xtal:/home/cad# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  xulrunner-1.9.2
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 24.9 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 282389 files and directories currently installed.)
Removing xulrunner-1.9.2 (1.9.2.28+build1+nobinonly-0ubuntu0.10.04.1) ...
/var/lib/dpkg/info/xulrunner-1.9.2.prerm: 8: /var/lib/dpkg/info/xulrunner-1.9.2.prerm: /usr/sbin/update-alternatives: not found
dpkg: error processing package xulrunner-1.9.2 (--remove):
 subprocess installed pre-removal script returned error exit status 127
/usr/lib/xulrunner-1.9.2.28/xulrunner-bin: error while loading shared libraries: libhunspell-1.2.so.0: cannot open shared object file: No such file or directory
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
cad-xtal:/home/cad# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 xulrunner-1.9.2 : Depends: libhunspell-1.2-0 (>= 1.2.8) but it is not installable
E: Unmet dependencies. Try using -f.
cad-xtal:/home/cad# sudo apt-get dist-upgrade

---

### Post by jmaciak1987 on 2015-02-20
Glad to see you have the same problem. From what I've read, I believe it's because xulrunner is requiring libhunspell1.2, yet 1.3 is installed. Not sure how to fix this yet.

---

### Post by chris_davis3 on 2015-02-20
Fun for us! I can't believe we're the only ones with the problem so far. Gosh, I've tried everything to no avail.

---

### Post by chris_davis3 on 2015-02-20
The following packages have unmet dependencies:

xulrunner-1.9.2: Depends: libatk1.0-0 (>= 1.29.3) but 2.10.0-2ubuntu2 is installed
                 Depends: libc6 (>= 2.11) but 2.19-0ubuntu6.5 is installed
                 Depends: libfontconfig1 (>= 2.8.0) but 2.11.0-0ubuntu4.1 is installed
                 Depends: libfreetype6 (>= 2.2.1) but 2.5.2-1ubuntu2.3 is installed
                 Depends: libgcc1 (>= 1:4.1.1) but 1:4.9.1-0ubuntu1 is installed
                 Depends: libglib2.0-0 (>= 2.23.5) but 2.40.2-0ubuntu1 is installed
                 Depends: libgtk2.0-0 (>= 2.18.0) but 2.24.23-0ubuntu1.1 is installed
                 Depends: libhunspell-1.2-0 (>= 1.2.8) but it is not installed
                 Depends: libnspr4-0d (>= 4.7.3-0ubuntu1~) but 2:4.10.7-0ubuntu0.14.04.1 is installed
                 Depends: libnss3-1d (>= 3.12.6) but 2:3.17.4-0ubuntu0.14.04.1 is installed
                 Depends: libpango1.0-0 (>= 1.14.0) but 1.36.3-1ubuntu1.1 is installed
                 Depends: libsqlite3-0 (>= 3.6.22) but 3.8.2-1ubuntu2 is installed
                 Depends: libstdc++6 (>= 4.1.1) but 4.8.2-19ubuntu1 is installed
                 Depends: zlib1g (>= 1:1.1.4) but 1:1.2.8.dfsg-1ubuntu1 is installed

---

### Post by chris_davis3 on 2015-02-20
[http://askubuntu.com/questions/452629/i-cant-install-xulrunner-1-9-2-on-ubuntu-14-04](http://askubuntu.com/questions/452629/i-cant-install-xulrunner-1-9-2-on-ubuntu-14-04)

This seems to work for me

---

### Post by jmaciak1987 on 2015-02-23
Bravo sir! That did it. Thanks :)

---

