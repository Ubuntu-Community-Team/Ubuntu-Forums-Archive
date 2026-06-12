---
title: "Services disable on reboot"
date: 2015-05-27
forum: Server Platforms
---

### Post by Halfdemon on 2015-05-27
I'm setting up a server and now for some reason whenever I reboot multiple services are disabled including apache2, mysql, acpid and I'm sure some others that I didn't know were enabled. There is a custom service called multicraft that works but does not report status correctly. It happened after I edited my /etc/init/rc-sysinit.conf file as per [this]("http://serverfault.com/questions/100240/services-not-starting-on-boot-but-will-start-manually-on-ubuntu-9-10") to no effect. I changed it back to a backed up original but it does not seem to have repaired the issue. I have re-enabled the services, re installed the service after purging it to no avail. Any help is greatly appreciated.

This is the output of "service --status-all" is shortly after a reboot.
```

 [ - ]  acpid
 [ - ]  apache2
 [ - ]  apparmor
 [ ? ]  apport
 [ - ]  atd
 [ - ]  bind9
 [ ? ]  console-setup
 [ + ]  cron
 [ - ]  dbus
 [ - ]  example
 [ + ]  friendly-recovery
 [ - ]  grub-common
 [ - ]  hddtemp
 [ - ]  ipmievd
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ ? ]  kmod
 [ - ]  mdadm
 [ ? ]  mdadm-waitidle
 [ - ]  multicraft
 [ ? ]  mysql
 [ ? ]  networking
 [ ? ]  ondemand
 [ - ]  procps
 [ ? ]  rc.local
 [ - ]  rsync
 [ - ]  rsyslog
 [ ? ]  screen-cleanup
 [ + ]  sendmail
 [ ? ]  sendsigs
 [ - ]  smartmontools
 [ - ]  snort
 [ - ]  ssh
 [ - ]  sudo
 [ - ]  udev
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  unattended-upgrades
 [ - ]  urandom
```

---

