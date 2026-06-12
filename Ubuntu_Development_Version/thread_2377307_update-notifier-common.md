---
title: "update-notifier-common"
date: 2017-11-11
forum: Ubuntu Development Version
---

### Post by #&amp;thj^% on 2017-11-11
Has any one seen this yet:
update-notifier-common has seemly lost it's path.
```
Setting up update-notifier-common (3.186) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debconf
ModuleNotFoundError: No module named 'debconf'
dpkg: error processing package update-notifier-common (--configure):
 installed update-notifier-common package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 update-notifier-common
```
Thought this might be due to python3 installation is broken. But when I:
```
type python3
python3 is /usr/bin/python3

```
So far looking OK....So I now look at the module and find:
```
python3 -m debconf
/usr/bin/python3: No module named debconf

```
And this:
```
apt policy update-notifier-common
update-notifier-common:
  Installed: 3.186
  Candidate: 3.186
```
But Installing things Like lets say "plank" I get:
```
sudo apt install plank
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopencv-imgproc3.2 libpango1.0-0 libpangox-1.0-0
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  bamfdaemon libbamf3-2 libplank-common libplank1
Suggested packages:
  libplank-doc
The following NEW packages will be installed:
  bamfdaemon libbamf3-2 libplank-common libplank1 plank
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 520 kB of archives.
After this operation, 2,198 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 libbamf3-2 amd64 0.5.3+17.10.20170810-0ubuntu1 [52.0 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 bamfdaemon amd64 0.5.3+17.10.20170810-0ubuntu1 [86.4 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 libplank-common all 0.11.4-1 [54.3 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 libplank1 amd64 0.11.4-1 [242 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 plank amd64 0.11.4-1 [86.0 kB]
Fetched 520 kB in 1s (269 kB/s)
Selecting previously unselected package libbamf3-2:amd64.
(Reading database ... 128145 files and directories currently installed.)
Preparing to unpack .../libbamf3-2_0.5.3+17.10.20170810-0ubuntu1_amd64.deb ...
Unpacking libbamf3-2:amd64 (0.5.3+17.10.20170810-0ubuntu1) ...
Selecting previously unselected package bamfdaemon.
Preparing to unpack .../bamfdaemon_0.5.3+17.10.20170810-0ubuntu1_amd64.deb ...
Unpacking bamfdaemon (0.5.3+17.10.20170810-0ubuntu1) ...
Selecting previously unselected package libplank-common.
Preparing to unpack .../libplank-common_0.11.4-1_all.deb ...
Unpacking libplank-common (0.11.4-1) ...
Selecting previously unselected package libplank1:amd64.
Preparing to unpack .../libplank1_0.11.4-1_amd64.deb ...
Unpacking libplank1:amd64 (0.11.4-1) ...
Selecting previously unselected package plank.
Preparing to unpack .../plank_0.11.4-1_amd64.deb ...
Unpacking plank (0.11.4-1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Setting up update-notifier-common (3.186) ...
Traceback (most recent call last):
  File "/usr/lib/update-notifier/package-data-downloader", line 26, in <module>
    import debconf
ModuleNotFoundError: No module named 'debconf'
dpkg: error processing package update-notifier-common (--configure):
 installed update-notifier-common package post-installation script subprocess returned error exit status 1
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.54.1-1ubuntu1) ...
Processing triggers for libc-bin (2.26-0ubuntu2) ...
Setting up libplank-common (0.11.4-1) ...
Processing triggers for man-db (2.7.6.1-2) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Processing triggers for hicolor-icon-theme (0.17-1) ...
Setting up libbamf3-2:amd64 (0.5.3+17.10.20170810-0ubuntu1) ...
Setting up bamfdaemon (0.5.3+17.10.20170810-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up libplank1:amd64 (0.11.4-1) ...
Setting up plank (0.11.4-1) ...
Processing triggers for libc-bin (2.26-0ubuntu2) ...
Errors were encountered while processing:
 update-notifier-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
EDIT Oh ya Line 26 looks like this:
```
import debconf
```

---

### Post by Frogs Hair on 2017-11-11
I experienced a crash , but the ability to update or install is not effected. "Problem Already Known"

---

### Post by #&amp;thj^% on 2017-11-11
> **Frogs Hair said:**
> I experienced a crash , but the ability to update or install is not effected.

Thanks! :) And yes I too can install and remove things just the annoying error:
```
Errors were encountered while processing:
 update-notifier-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Looks like we both sent the report in.

---

### Post by Frogs Hair on 2017-11-11
Just installed. ```
sudo apt install htop[sudo] password for d-book: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  htop
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 76.6 kB of archives.
After this operation, 216 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 htop amd64 2.0.2-1 [76.6 kB]
Fetched 76.6 kB in 0s (264 kB/s)
Selecting previously unselected package htop.
(Reading database ... 244767 files and directories currently installed.)
Preparing to unpack .../htop_2.0.2-1_amd64.deb ...
Unpacking htop (2.0.2-1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.3+17.10.20170810-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.7.6.1-2) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Setting up htop (2.0.2-1) ...



```

---

### Post by Kris_M on 2017-11-11
> **1fallen said:**
> Thanks! :) And yes I too can install and remove things just the annoying error:
```
Errors were encountered while processing:
 update-notifier-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Looks like we both sent the report in.

I remember running in to that early on with 18.04 when I was having problems getting rid of the mscorefont messages. I believe I had deleted/renamed a module, and things went south. It did mess everything up.  Ultimately I restored (clonezilla) to before problem and it was thus fixed.
/var/lib/update-notifier/package-data-downloads/

---

### Post by dino99 on 2017-11-12
Opened report: [https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1731334](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/1731334)

---

### Post by mc4man on 2017-11-12
Seems simple - you upgraded apt* & debconf from -proposed before they where ready to be used. Downgrade & the issue will go away or wait it out.
(apt* should be @ 1.5.1, debconf @ 1.5.63

---

### Post by zika on 2017-11-12
Or go to apt 1.6 and debconf 1.5.64... ;)
[SIZE=1]Not joking but also no guarantee given... ;)[/SIZE]
apt (1.6~alpha4) unstable; urgency=medium  
debconf (1.5.64) unstable; urgency=medium
 
Update&#8321;: 
[COLOR=#000000]apt (1.6~alpha5) unstable; urgency=medium
[/COLOR][COLOR=#000000]debconf (1.5.64ubuntu2) bionic; urgency=medium[/COLOR] 
 * Add Breaks: against update-notifier-common (<< 3.187) for the migration
    of the python module.  LP: #1731334.

---

