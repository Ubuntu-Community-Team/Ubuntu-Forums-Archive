---
title: "Upgrade to 17.11 Fails - gzip Problem"
date: 2007-02-13
forum: Repositories &amp; Backports
---

### Post by OldSeaDog on 2007-02-13
I see others have come to grief or ran aground or whatever upgrading their boxes to 17.11.  My particular bit of grief ends real early.  I have tried to upgrade using Update Manager, Synaptic and apt directly, all with the same result.  BTW, before running any of them, I ran apt-get update to ensure I had the correct lists.

From apt-get upgrade the specific process message is:

whoever@BigBertha:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  linux-headers-386 linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  bind9-host dnsutils gtk2-engines-pixbuf kdelibs-data kdelibs4c2a kubuntu-default-settings language-pack-en language-pack-gnome-en libbind9-0 libdns21
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libisc11 libisccc0 libisccfg1 liblwres9
  libpq4 libsmbclient libwxbase2.6-0 libwxgtk2.6-0 linux-generic linux-restricted-modules-common linux-source nvidia-kernel-source popularity-contest
  postgresql-8.1 postgresql-client-8.1 postgresql-client-common postgresql-common python-wxversion samba-common smbclient spampd wine
39 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
6 not fully installed or removed.
Need to get 0B/55.2MB of archives.
After unpacking 983kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Reading package fields... Done
Reading package status... Done
Retrieving bug reports... 0% [0/39] W: not in gzip format: libgtk2.0-common
 W: not in gzip format: spampd
 W: not in gzip format: kdelibs-data
 W: not in gzip format: libisccfg1
 W: not in gzip format: smbclient
 W: not in gzip format: language-pack-en
 W: not in gzip format: wine
 W: not in gzip format: gtk2-engines-pixbuf
 W: not in gzip format: liblwres9
 ... E: Too many errors while retrieving bug reports
E: Sub-process if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi returned an error code (10)
E: Failure running script if dpkg -s apt-listbugs | grep -q '^Status: .* ok installed'; then /usr/sbin/apt-listbugs apt || ( test $? -ne 10 || exit 10; echo 'Warning: apt-listbugs exited abnormally, hit enter key to continue.' 1>&2 ; read a < /dev/tty ); fi .

The download was never a problem, the files have been downloaded, either from the Canadian mirror or from ubuntu.com directly.  However, when it comes to the unpacking and installing, things are a lot less cheery.  Anyone have a thought on how I can cheer myself (and BigBertha) up?

OldSeaDog, the Geekosaur

---

### Post by OldSeaDog on 2007-02-13
I should add for completeness that I have an ASUS M2N SLIDeluxr motherboard and an AMD 4200+ processor with 2 GB of RAM.  I am using a Foxconn/NVidiaGeFore GT 7300 video card.  I havean ide 250GB hard drive off a JMicron controller and a 320 GB SATA hard drive off an NVidia controller.  I am running Edgy.

---

