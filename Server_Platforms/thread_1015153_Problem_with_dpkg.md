---
title: "Problem with dpkg"
date: 2008-12-18
forum: Server Platforms
---

### Post by keymoo on 2008-12-18
Hi there, I'm using Hardy Server.

When I run this command

```
apt-get -y -f upgrade
```I get these errors:

[FONT=Courier New]Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-image-server linux-server openssh-client openssh-server ssl-cert
The following packages will be upgraded:
  bind9-host clamav clamav-base clamav-freshclam cupsys cupsys-bsd
  cupsys-client cupsys-common grub initramfs-tools libapache2-mod-php5
  libclamav3 libcupsimage2 libcupsys2 libcupsys2-dev libdbus-1-3 libgnutls-dev
  libgnutls13 libgnutlsxx13 libmysqlclient15off libpq5 libxml2 linux-libc-dev
  login logrotate module-init-tools mysql-client-5.0 mysql-common mysql-server
  mysql-server-5.0 nfs-common nfs-kernel-server passwd php5 php5-common
  php5-mysql python-apt samba samba-common smbclient smbfs
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin: 
41 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
3 not fully installed or removed.
Need to get 0B/74.5MB of archives.
After this operation, 512kB of additional disk space will be used.
[/FONT] [FONT=Courier New][COLOR=Red](Reading database ... dpkg: error processing /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb (--unpack):
 files list file for package `clamav' is missing final newline[/COLOR][/FONT][FONT=Courier New]
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-common_5.0.51a-3ubuntu5.4_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)[/FONT]

Any ideas on how to fix it? Thanks.

---

