---
title: "latest update rips libre icons from Unity launcer-tryingto recover"
date: 2012-01-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2012-01-12
Just had an update where '10' updates were to be removed. I should no better but I just went ahead anyways. :)

---

### Post by ventrical on 2012-01-12
Here it is...

---

### Post by ventrical on 2012-01-12
Here are ripped icons..

---

### Post by zika on 2012-01-12
[http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by ventrical on 2012-01-12
> **zika said:**
> [http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)


heheh.. thanks zika. 

```
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libx264-116 libgoa-1.0-common openoffice.org-common python-central
  libmagickcore3 libmagickwand3 libmagickcore3-extra libreoffice-l10n-common
  libmatroska4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-core
The following packages will be upgraded:
  libreoffice-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0 B/37.3 MB of archives.
After this operation, 2,512 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 348372 files and directories currently installed.)
Preparing to replace libreoffice-core 1:3.4.4-0ubuntu2 (using .../libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb) ...
rmdir: failed to remove `usr/lib/libreoffice/basis3.4/program/': Directory not empty
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb
Error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@dale-desktop:~$ 

```

---

### Post by ventrical on 2012-01-12
Apport filed this ..

[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915466](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915466)

---

### Post by ventrical on 2012-01-12
Nope .... I an remove it but I can't install it.



Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.0~beta2-2ubuntu2_i386.deb

---

### Post by ventrical on 2012-01-12
Ok...  I had to go to libreoffice web site:

[http://www.libreoffice.org/download/](http://www.libreoffice.org/download/)

download those files and then install them. whew ! What a job. then , THEN .. as I am working away at this. all of a sudden. I have these multiple widows open and I accidently double clicked my scroll wheel while I was moving somthing  and then all of a sudden the desktop does this weird application-compiz switcher  on me and this is a blacklisted card and I'm using the Unity 2D desktop... so mabey I'm just tired or somthing .. :) but I think compiz-pligins is trying to come on through into Unity 2D now so be on the lookout .!

didn't have my camera on .. ;(

---

### Post by lonniehenry on 2012-01-12
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915271](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915271) post#7 works for those who get hung up by this problem. It installs the the new programs.  Thanks to zval for the solution.

---

### Post by ventrical on 2012-01-12
> **lonniehenry said:**
> [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915271](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/915271) post#7 works for those who get hung up by this problem. It installs the the new programs.  Thanks to zval for the solution.

nope .. that workaround didn' work here .. but thanks so much .. I have it manually fixed for now.

---

