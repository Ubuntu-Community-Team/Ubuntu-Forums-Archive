---
title: "Problem with updating package with apt-get"
date: 2011-05-08
forum: Server Platforms
---

### Post by eparra on 2011-05-08
I have been using the following repository in /etc/apt/sources.list for Asterisk 1.8:

deb [http://ppa.launchpad.net/dajhorn/pkg-voip/ubuntu](http://ppa.launchpad.net/dajhorn/pkg-voip/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/dajhorn/pkg-voip/ubuntu](http://ppa.launchpad.net/dajhorn/pkg-voip/ubuntu) lucid main 

Everything has been working fine for a few months and recently I had an issue updating it. I have tried removing it, but with no success. How can I fix this - even if it means removing all Asterisk1.8 packages and reinstalling?

**eparra@dev:~$ sudo apt-get upgrade**
Reading package lists... Done
Building dependency tree 
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
[COLOR="Red"]The following packages have unmet dependencies:
asterisk1.8: Depends: asterisk1.8-config (= 1.8.1.1-lucid.dajhorn6) but 1.8.3.3-0ubuntu1~lucid1 is installed or
asterisk-config-custom but it is not installable
E: Unmet dependencies. Try using -f.[/COLOR]
**eparra@dev:~$ sudo apt-get upgrade -f**
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies... Done
The following packages have been kept back:
gearman-job-server
The following packages will be upgraded:
asterisk1.8
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
29 not fully installed or removed.
Need to get 0B/3,965kB of archives.
After this operation, 1,716kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 84683 files and directories currently installed.)
Preparing to replace asterisk1.8 1.8.1.1-lucid.dajhorn6 (using .../asterisk1.8_1.8.3.3-0ubuntu1~lucid1_i386.deb) ...
[COLOR="red"]Unpacking replacement asterisk1.8 ...
dpkg: error processing /var/cache/apt/archives/asterisk1.8_1.8.3.3-0ubuntu1~lucid1_i386.deb (--unpack):
trying to overwrite '/usr/lib/asterisk/modules/cdr_mysql.so', which is also in package asterisk1.8-mysql 0:1.8.3.3-0ubuntu1~lucid1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
/var/cache/apt/archives/asterisk1.8_1.8.3.3-0ubuntu1~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
**eparra@dev:~$ sudo apt-get -f install**
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
linux-headers-2.6.32-24 honeyd-common libdumbnet1 linux-headers-2.6.32-24-generic-pae farpd libreadline5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
asterisk1.8
Suggested packages:
asterisk1.8-doc asterisk1.8-dev asterisk1.8-h323
The following packages will be upgraded:
asterisk1.8
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
29 not fully installed or removed.
Need to get 0B/3,965kB of archives.
After this operation, 1,716kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 84683 files and directories currently installed.)
Preparing to replace asterisk1.8 1.8.1.1-lucid.dajhorn6 (using .../asterisk1.8_1.8.3.3-0ubuntu1~lucid1_i386.deb) ...
[COLOR="red"]Unpacking replacement asterisk1.8 ...
dpkg: error processing /var/cache/apt/archives/asterisk1.8_1.8.3.3-0ubuntu1~lucid1_i386.deb (--unpack):
trying to overwrite '/usr/lib/asterisk/modules/cdr_mysql.so', which is also in package asterisk1.8-mysql 0:1.8.3.3-0ubuntu1~lucid1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
/var/cache/apt/archives/asterisk1.8_1.8.3.3-0ubuntu1~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]
eparra@dev:~$

---

### Post by falko on 2011-05-09
You could try apt-pinning: [http://www.howtoforge.com/a-short-introduction-to-apt-pinning](http://www.howtoforge.com/a-short-introduction-to-apt-pinning)

---

