---
title: "lighttpd + php5 dist-upgrade needs apache2.2-common?"
date: 2009-09-01
forum: Server Platforms
---

### Post by aoakley on 2009-09-01
Hi, I ran apt-get update && apt-get dist-upgrade on my Ubuntu Hardy 8.04.3 server this evening, and suddenly it wants to install apache2.2-common .

I have lighttpd and php5 installed on my server. lighttpd is my web server, and I do not want to install apache.

Is this a new dependency problem? Should I report it as a bug, if so where and how? Alternatively, how can I perform this dist-upgrade without installing apache? Thanks.

```
root@isis:~# date
Tue Sep  1 22:13:16 BST 2009
root@isis:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  apache2-mpm-prefork apache2.2-common libapache2-mod-php5
The following packages will be upgraded:
  kdelibs-data kdelibs4c2a libc6 libc6-dev libc6-i686 libcurl3 libcurl3-gnutls
  libgnutls13 libvorbis0a libvorbisenc2 libvorbisfile3 libxml2 linux-libc-dev
  php-pear php5 php5-cgi php5-cli php5-common php5-curl php5-dev php5-gd
  php5-mysql php5-sqlite php5-xmlrpc php5-xsl tzdata
26 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 41.0MB of archives.
After this operation, 9503kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
root@isis:~# deborphan -a
main/utils                sysutils
main/net                  telnet
main/interpreters         tcl8.4
main/sound                mp3info
main/graphics             mplayer-nogui
non-free/doc              manpages-posix
main/web                  php5-imagick
main/misc                 chkrootkit
main/web                  php5-sqlite3
main/web                  php5-gd
main/web                  php5-suhosin
main/web                  php5-sqlite
main/web                  php5-xmlrpc
non-free/utils            rar
main/net                  tinyproxy
main/net                  portmap
main/net                  rsync
main/web                  php5-curl
main/web                  lighttpd
main/utils                db4.6-util
main/web                  vlogger
main/net                  bind9-host
main/net                  ntp
main/web                  php5-memcache
main/misc                 screen
main/utils                debian-helper-scripts
main/admin                pwgen
main/admin                command-not-found
main/net                  ldap-utils
main/utils                syslinux
main/shells               tcsh
main/doc                  info
main/net                  iputils-ping
main/net                  iputils-tracepath
main/admin                dselect
main/utils                rdiff-backup
main/web                  php5-xsl
main/graphics             imagemagick
main/editors              nano
main/utils                daemon
main/net                  ntpdate
main/web                  php5
main/misc                 libpam-foreground
main/net                  fail2ban
main/text                 patchutils
main/sound                lame
main/mail                 msmtp
main/utils                strace
main/misc                 mysql-server
main/web                  php5-mysql
main/admin                deborphan
main/admin                quotatool
main/net                  netcat
main/utils                lsof
main/admin                rkhunter
```

---

### Post by Bachstelze on 2009-09-01
[http://packages.ubuntu.com/hardy-updates/php5](http://packages.ubuntu.com/hardy-updates/php5)

Indeed, the new php5 depends on libapache2-mod-php5. You can safely uninstall it (it is just a metapackage), and it shouldn't bother you anymore. Maybe you could file a bug too, see instructions here;

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by aoakley on 2009-09-02
Thanks. Bug submitted:

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/423071](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/423071)

---

### Post by Bachstelze on 2009-09-02
> **aoakley said:**
> Thanks. Bug submitted:

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/423071](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/423071)

As I said, you can just uninstall php5 and proceed with the upgrade. It is just a metapackage, meaning that it doesn't contain anything by itself.

---

