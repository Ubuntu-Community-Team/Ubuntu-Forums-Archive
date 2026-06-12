---
title: "Can't access FTP"
date: 2005-12-15
forum: Server Platforms
---

### Post by Liberteh on 2005-12-15
Hai,

I've installed 3 FTP servers already, but none work, everytime I get "connection refused". my ports are open.

Can somebody help?

---

### Post by bjweeks on 2005-12-15
Your going to have to give more info than that.

---

### Post by Liberteh on 2005-12-15
like?

---

### Post by bjweeks on 2005-12-15
First are you trying to connect on a lan or over the internet?

---

### Post by Liberteh on 2005-12-15
local, and tried lan, AND a friend tried, none worked

---

### Post by alamba on 2005-12-15
Paste the output of the following:
1. nmap localhost
2. ls /etc/init.d
3. ps -ef | grep <name_of_ftp_server_u_Installed>

Akshay

---

### Post by Liberteh on 2005-12-15
Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-12-15 14:27 CET
Interesting ports on wololo.local (127.0.0.1):
(The 1647 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
53/tcp    open  domain
80/tcp    open  http
110/tcp   open  pop3
111/tcp   open  rpcbind
139/tcp   open  netbios-ssn
143/tcp   open  imap
445/tcp   open  microsoft-ds
631/tcp   open  ipp
938/tcp   open  unknown
953/tcp   open  rndc
3306/tcp  open  mysql
6667/tcp  open  irc
10000/tcp open  snet-sensor-mgmt
32770/tcp open  sometimes-rpc3

Nmap finished: 1 IP address (1 host up) scanned in 0.359 seconds


##############################################

root@wololo:/home/liberty/eggdrop1.6.17# ls /etc/init.d
acpid         checkfs.sh          gdm              ircd-ircu                        networking         quota           single         vbesave
acpi-support  checkroot.sh        halt             keymap.sh                        nfs-common         quotarpc        skeleton       vhcs2_daemon
alsa          console-screen.sh   hdparm           klogd                            nfs-kernel-server  rc              spamassassin   vhcs2_network
alsa-utils    courier-authdaemon  hostname.sh      linux-restricted-modules-common  ntpdate            rcS             ssh            webmin
anacron       courier-imap        hotkey-setup     lvm                              pcmcia             readahead       stop-bootlogd  wu-ftpd
apache2       courier-pop         hotplug          makedev                          portmap            README          sudo           xorg-common
apmd          cron                hotplug-net      mdadm                            postfix            reboot          sysklogd
atd           cupsys              hplip            mdadm-raid                       postgresql-7.4     rmnologin       udev
bind9         dbus                hwclockfirst.sh  module-init-tools                powernowd          rsync           udev-mtab
bluez-utils   dhcp3-server        hwclock.sh       mountall.sh                      ppp                samba           umountfs
bootclean.sh  dns-clean           ifrename         mountnfs.sh                      pppd-dns           saslauthd       umountnfs.sh
bootlogd      evms                ifupdown         mountvirtfs                      procps.sh          screen-cleanup  urandom
bootmisc.sh   fetchmail           ifupdown-clean   mysql                            proftpd            sendsigs        usplash


###############################################


root@wololo:/home/liberty/eggdrop1.6.17# ps -ef | grep pro-ftpd
root     29185   463  0 14:28 pts/1    00:00:00 grep pro-ftpd

---

### Post by NotJustANewbie on 2005-12-15
nmap showed that port 21 (FTP) was not open. This may be the problem. Are you using any firewall that may stop the incoming traffic?

---

### Post by Liberteh on 2005-12-15
Nope.. not on Linux.. and I opened the port on my router some time ago

---

