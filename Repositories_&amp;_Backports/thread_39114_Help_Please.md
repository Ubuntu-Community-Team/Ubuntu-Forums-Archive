---
title: "Help Please"
date: 2005-06-03
forum: Repositories &amp; Backports
---

### Post by bluecode77 on 2005-06-03
i cant install new software cause synaptic keeps giving me error that there are fglrx-control is missing,
I tried to reinstall
none of them worked.

How would i comever this problem?
Because of that error i cant install new files
thanks

---

### Post by Martin Witte on 2005-06-03
Try ' sudo apt-get install fglrx-control' in a terminal window.

---

### Post by bluecode77 on 2005-06-03
I have tried,, you shall see the output down:
root@darkstar:/home/alper # sudo apt-get install fglrx-cpntrol
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fglrx-cpntrol
root@darkstar:/home/alper # sudo apt-get install fglrx-control
Reading package lists... Done
Building dependency tree... Done
fglrx-control is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up ttf-indic-fonts (0.3.7ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format errordpkg: error processing ttf-indic-fonts (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ttf-indic-fonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@darkstar:/home/alper #

I am really getting desperate about it.. how would i resolve that problem...

---

