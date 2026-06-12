---
title: "Ubuntu 20.04 LTS Missing ldif2db after Installation of 389-ds-(base)"
date: 2022-07-06
forum: Server Platforms
---

### Post by sesche on 2022-07-06
Hi everyone

We are migrating a dogtag-pki from CentOS to a up-to-date Ubuntu 20.04 LTS. Dogtag needs 389-ds Directory Server to store its data. Installing 386-ds went without any problems, after that you have to use the Installationscript [FONT=courier new][COLOR=#000000]/usr/shar/dirsrv/setup-ds.pl[/COLOR][/FONT] to install an instance.

But the Setup fails with a missing file message [FONT=courier new][COLOR=#000000]/etc/dirsrv/config/template-initconfig[/COLOR][/FONT]. Google said it is a known bug [https://bugs.launchpad.net/ubuntu/+source/389-ds-base/+bug/1972014](https://bugs.launchpad.net/ubuntu/+source/389-ds-base/+bug/1972014) which is not solved yet. But I was able to copy the template file from another installation.

Now to the unsolved problem, the next try to run the setup script, told me that ldif2db file is missing. Some further investigation showed that on 20.04 ldif2db is not included anymore in the 386-ds package (still was in the bionic/18.04 Version) [https://packages.ubuntu.com/search?suite=bionic&arch=any&searchon=contents&keywords=ldif2db](https://packages.ubuntu.com/search?suite=bionic&arch=any&searchon=contents&keywords=ldif2db). This makes no sense to me, that a file which is needed to install a new instance is not included in the package. 

What am I missing? Does anyone has a hint for me? 

Thanks for your help

---

### Post by TheFu on 2022-07-06
Complain to the 386-ds maintainer.  I doubt Canonical touches that package at all.  It isn't part of the core libraries.

```
$ apt search 386-ds
Sorting... Done
Full Text Search... Done
```

I checked on both 20.04 Server and on a 20.04 Desktop with default APT repo settings.

---

### Post by rsteinmetz70112 on 2022-07-06
I don't know this package, but have you checked the template file you copied? Was it from an identical version of the package installed on Ubuntu?

---

### Post by sesche on 2022-07-08
Thanks for your answers, after a couple of hours of trying, the solution to this problem is quite simple. I used ds-setup.pl which uses ldif2db in the background, which didn't work, even if i had a good documentation from my last install on CentOS. 

[B]So the Problem was RTFM! 
[/B]
After trying to get it run for several hours I started with a clean install and used the correct Installation Documentation on the Dogtag Site. So ds-setup.pl is the installation routine from Version 1.3 which unfortunately is still in the package. For the 1.4 Version you have to use the dscreate command.

So this thread can be closed, thanks for your help and shame on me for bothering you guys with a problem that sat in front of the Keyboard. ;-)

---

### Post by TheFu on 2022-07-08
a) Please open a bug report that the script is still in the new package with the package maintainer team.

b) Whenever a problem is solved here, please use the Thread Tools Button to mark it "SOLVED" to help the community. Both people seeking answers and people wishing to help won't waste time on "SOLVED" threads.  Only the thread originator can do this.

---

### Post by sesche on 2022-07-08
Thanks TheFU, I put it on solved, about reporting the bug. In Ubuntu 20.04.4 LTS the current Version of 389.ds is 1.4.3.6-2. On the maintainers website you will get Version 1.4.3.23 (May 2021) and the most current is Version 2.2.2. In Version 1.4.3.18 an issue is fixed with ldif2db, which means ldif2db ist still in the package. So this is probably more of an issue of the old version which is used in ubuntu 20.04

---

### Post by odinn-burkni on 2023-02-09
Hi guys,
I've installed 389-ds on 22.04 server.
I installed it this way:
sudo apt install 389-ds
and then 
sudo apt install cockpit-doc cockpit-pcp cockpit-sosreport xdg-utils udisks2-lvm2 sssd-dbus apache2 pcscd lm-sensors snmp-mibs-downloader m4-doc make-doc avahi-autoipd libteam-utils python-networkx-doc python3-gdal python3-matplotlib python3-pydot python3-pygraphviz python3-scipy gcc gfortran python-numpy-doc python3-dev subversion python-pygments-doc ttf-bitstream-vera setools-gui wpagui libengine-pkcs11-openssl 

I then used this tutorial to create an instance: [https://documentation.suse.com/sles/15-SP3/html/SLES-all/cha-security-ldap.html#sec-security-ldap-server-template](https://documentation.suse.com/sles/15-SP3/html/SLES-all/cha-security-ldap.html#sec-security-ldap-server-template)
sudo dscreate create-template myInstance.txt
I then changed some things in the file, like giving my instance a name and put in the password and such.
sudo dscreate from-file myInstance.txt

This seemed to work fine and this command sudo dsctl myInstance status, shows that my instance is up and running.
When I go to the webgui, it comes up with the Apache2 Ubuntu Default Page: It works!  using :9830 or :3890 leads to nothing. I'm pretty sure I'm missing some step regarding setting up Apache. I blame it on tiredness. Can anyone point me in the right direction?

Thanks in advance...

---

### Post by QIII on 2023-02-09
Hello!

Adding a post to a thread that was marked as solved 7 months ago is not a good way to attract attention.

Please start your own thread.  Thanks.

As for this thread -- Rest in Peace.

Closed.

---

