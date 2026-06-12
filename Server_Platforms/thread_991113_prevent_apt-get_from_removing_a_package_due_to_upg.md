---
title: "prevent apt-get from removing a package due to upgrade"
date: 2008-11-23
forum: Server Platforms
---

### Post by jemmrich on 2008-11-23
Hi everyone,

I am trying to upgrade my server from php4 to php5 like so:

> server:~# apt-get install php5
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libapache2-mod-php5
The following packages will be REMOVED:
  libapache2-mod-php4 vhcs vhcs-daemon vhcs-gui vhcs-gui-pma
The following NEW packages will be installed:
  libapache2-mod-php5 php5
0 upgraded, 2 newly installed, 5 to remove and 1 not upgraded.
Need to get 0B/2414kB of archives.
After unpacking 20.3MB disk space will be freed.
Do you want to continue [Y/n]?

How can I upgrade php4 to php5 without losing my vhcs install?

This is an in production server so I am less adventurous when it comes to package management.

Thanks
James

---

### Post by jpkotta on 2008-11-23
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

Also, it may be that the vhcs packages were pulled in as a dependency of libapache2-mod-php4.  In that case it is probably enough to explicitly install them.  Then they won't be removed as unused deps when the libapache2-mod-php4 is removed.

---

### Post by jemmrich on 2008-11-23
> **jpkotta said:**
> [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-pin)

Also, it may be that the vhcs packages were pulled in as a dependency of libapache2-mod-php4.  In that case it is probably enough to explicitly install them.  Then they won't be removed as unused deps when the libapache2-mod-php4 is removed.

It looks like vhcs depends on libapache2-mod-php4 as 

apt-rdepends libapache2-mod-php4

does not reference vhcs in any way.

Here is the output of apt-rdepends vhcs
[http://www.pastebin.ca/1265237](http://www.pastebin.ca/1265237)

I read the man pages on apt_preferences but still don't quite understand the pin priority.

Based from what I understand of the link you posted, does this look correct?

Package: vhcs
Pin: vhcs 2.4.3-1
Pin-Priority: 1001

It sounds like it keeps it from being upgraded, but not sure about being removed.

Thanks for the help,
James

---

### Post by jemmrich on 2008-11-23
just an update to my previous post my /etc/apt/preferences file looks like this:

Package: vhcs
Pin: version 2.4.7.1-2
Pin-Priority: 1001

however apt still wants to remove vhcs when i do this:

server:/etc/apt# apt-get -s install php5
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libapache2-mod-php5
The following packages will be REMOVED:
  libapache2-mod-php4 vhcs vhcs-daemon vhcs-gui vhcs-gui-pma
The following NEW packages will be installed:
  libapache2-mod-php5 php5
0 upgraded, 2 newly installed, 5 to remove and 1 not upgraded.
Remv vhcs-gui-pma [2.4.7.1-2]
Remv vhcs-gui [2.4.7.1-2] [vhcs ]
Remv vhcs [2.4.7.1-2] [vhcs-daemon ]
Remv vhcs-daemon [2.4.7.1-2]
Remv libapache2-mod-php4 [6:4.4.4-8+etch6]
Inst libapache2-mod-php5 (5.2.0-8+etch13 Debian:4.0r5/stable, Debian-Security:4.0/stable)
Inst php5 (5.2.0-8+etch13 Debian:4.0r5/stable, Debian-Security:4.0/stable)
Conf libapache2-mod-php5 (5.2.0-8+etch13 Debian:4.0r5/stable, Debian-Security:4.0/stable)
Conf php5 (5.2.0-8+etch13 Debian:4.0r5/stable, Debian-Security:4.0/stable)

---

### Post by jpkotta on 2008-11-23
[http://vhcs.net/new/modules/wfchannel/index.php?pagenum=3](http://vhcs.net/new/modules/wfchannel/index.php?pagenum=3)
> PHP 4.x

So it probably depends on libapache2-mod-php4, which conflicts with libapache2-mod-php5, which in turn is a dep of php5.  There is probably a way to force this to work, but I don't know it.  

BTW, Ubuntu 8.04 and newer don't even have php4 in the repositories.

---

