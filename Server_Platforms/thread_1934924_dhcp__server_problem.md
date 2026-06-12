---
title: "dhcp  server problem"
date: 2012-03-03
forum: Server Platforms
---

### Post by mustafa ibrahim on 2012-03-03
hello
this is my release

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

i installed dhcp server it works good but now i want to disable it how really i make remove and purge and deleted my network in terface and it is still working with dhcp why???????????
this is my network interfaces

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.252
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 10.0.0.138
##############################################################################
auto eth0:138
iface eth0:138 inet static
 address 10.0.0.138
 netmask 255.255.255.0
# gateway 10.0.0.138
auto eth0:2
iface eth0:2 inet static
 address 10.0.2.1
 netmask 255.255.255.0
# gateway 192.168.1.1
#####################################
auto eth0:5
iface eth0:5 inet static
 address 10.0.5.1
 netmask 255.255.255.0
# gateway 192.168.1.1
####################################
auto eth0:7
iface eth0:7 inet static
 address 10.0.7.1
 netmask 255.255.255.0
 #gateway 192.168.1.1
####################################
auto eth0:6
iface eth0:6 inet static
 address 10.0.6.1
 netmask 255.255.255.0
 #gateway 192.168.1.1

please help

---

### Post by Iowan on 2012-03-03
If you are getting a DHCP address, **dhclient** may be responsible.

---

### Post by ksudbury on 2012-03-03
Hi Mustafa, 

See this [Ubuntu static IP address]("http://linuxmoz.com/ubuntu-static-ip/") tutorial it explains in detail how to stop Ubuntu getting it's IP address via DHCP and shows you how to correctly configure your /etc/network/interfaces file. 

Hope that helps :)

---

### Post by mustafa ibrahim on 2012-03-07
thanks for you replay but i think it is not usful to me 
look really i make purge and remove to my dhcp server and there is some thing wrong i do not know the problem tell me what to do and i f u are free i can open team viewer to u 
please give me your email address

---

### Post by mustafa ibrahim on 2012-03-07
service --status-all
 [ + ]  apache2
 [ + ]  apparmor
 [ ? ]  atd
 [ + ]  bind9
 [ - ]  bootlogd
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  dbus
 [ + ]  ddclient
 [ - ]  dhcp3-server
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  failsafe-x
 [ - ]  grub-common
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ ? ]  module-init-tools
 [ ? ]  mysql
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  networking
 [ ? ]  nmbd
 [ ? ]  ondemand
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ - ]  proftpd
 [ ? ]  rc.local
 [ - ]  rsync
 [ ? ]  rsyslog
 [ ? ]  sendsigs
 [ ? ]  smbd
 [ + ]  ssh
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  sudo

 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  urandom
 [ ? ]  vsftpd
 [ ? ]  webmin
 [ + ]  winbind
 [ - ]  x11-common
root@mustafa-sr1:/home/mustafa-sr1# service --status-all
 [ + ]  apache2
 [ + ]  apparmor
 [ ? ]  atd
 [ + ]  bind9
 [ - ]  bootlogd
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  dbus
 [ + ]  ddclient
 [ - ]  dhcp3-server
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  failsafe-x
 [ - ]  grub-common
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  irqbalance
 [ ? ]  killprocs
 [ ? ]  module-init-tools
 [ ? ]  mysql
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  networking
 [ ? ]  nmbd
 [ ? ]  ondemand
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  p [ ? ]  procps
 [ - ]  proftpd
 [ ? ]  rc.local
 [ - ]  rsync
 [ ? ]  rsyslog
 [ ? ]  sendsigs
 [ ? ]  smbd
 [ + ]  ssh
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  sudo
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ - ]  urandom
 [ ? ]  vsftpd
 [ ? ]  webmin
 [ + ]  winbind
 [ - ]  x11-common
ppd-dns

---

### Post by mustafa ibrahim on 2012-03-08
ok i found my prob that dhcp was installed in the router not in my server
thanks all

---

