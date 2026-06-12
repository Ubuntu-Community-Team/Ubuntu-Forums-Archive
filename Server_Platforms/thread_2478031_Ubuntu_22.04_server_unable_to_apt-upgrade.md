---
title: "Ubuntu 22.04 server unable to apt-upgrade"
date: 2022-08-15
forum: Server Platforms
---

### Post by deepakdeshp on 2022-08-15
Please see the command logs below. I am not able to upgrade the system. Please suggest.

```
  sudo apt upgrade Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 koha-common : Depends: libmarc-xml-perl but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
uma@ubuntu:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmarc-file-xml-perl linux-headers-5.15.0-25
  linux-headers-5.15.0-25-generic linux-image-5.15.0-25-generic
  linux-modules-5.15.0-25-generic linux-modules-extra-5.15.0-25-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libmarc-xml-perl
The following NEW packages will be installed:
  libmarc-xml-perl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
161 not fully installed or removed.
Need to get 0 B/16.5 kB of archives.
After this operation, 47.1 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 203475 files and directories currently installed.)
Preparing to unpack .../libmarc-xml-perl_1.0.5-2_all.deb ...
Unpacking libmarc-xml-perl (1.0.5-2) ...
dpkg: error processing archive /var/cache/apt/archives/libmarc-xml-perl_1.0.5-2_
all.deb (--unpack):
 trying to overwrite '/usr/bin/marc2xml', which is also in package libmarc-file-
xml-perl 1.0.5-1~koha+1
Errors were encountered while processing:
 /var/cache/apt/archives/libmarc-xml-perl_1.0.5-2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by deepakdeshp on 2022-08-15
Following command fixed it.```
 sudo dpkg -i --force-overwrite /var/cache/apt/archives/libmarc-xml-perl_1.0.5-2_all.deb  
```

---

