---
title: "Citadel Fails to start"
date: 2010-10-23
forum: Server Platforms
---

### Post by kin37ik on 2010-10-23
g'day, got citadel installed and everything like that, but just after the install, i got this:
 
 setup is finished, but the citadel server failed to start.
 Go back and check your configuration.
 
 
 
 
 
 as far as im concerned, my configuration should be fine, since the only thing i did change on the first time setup was requiring an administrator username and password, have any clue what might be going on?

---

### Post by HermanAB on 2010-10-23
Look at the citadel installation log file.

---

### Post by Horatio on 2011-04-29
I'm having a very similar problem. I noticed that the file, "/etc/init.d/citadel" does not exist. So I tried to reinstall citadel with:
```

$ sudo apt-get --reinstall  install citadel-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 18 not upgraded.
Need to get 0B/407kB of archives.
After this operation, 0B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 257012 files and directories currently installed.)
Preparing to replace citadel-server 7.72-3 (using .../citadel-server_7.72-3_amd64.deb) ...
Unpacking replacement citadel-server ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up citadel-server (7.72-3) ...
applying your settings.
Setup is finished, but the Citadel server failed to start.
Go back and check your configuration.

```

Although it is still not there.
```

$ ls | cat
acpid
acpi-support
alsa-mixer-save
anacron
apache2
apparmor
apport
atd
avahi-daemon
binfmt-support
bluetooth
bootlogd
brltty
clamav-daemon
clamav-freshclam
clamsmtp
console-setup
cron
cups
dbus
dmesg
dns-clean
etc-setserial
failsafe-x
fancontrol
grub-common
gssd
halt
hostname
hwclock
hwclock-save
idmapd
irqbalance
kdm
kerneloops
killprocs
lirc
lm-sensors
memcached
module-init-tools
mysql
networking
network-interface
network-interface-security
network-manager
nfs-kernel-server
ondemand
pcmciautils
plymouth
plymouth-log
plymouth-splash
plymouth-stop
portmap
portmap-boot
portmap-wait
postfix
pppd-dns
procps
pulseaudio
rc
rc.local
rcS
README
reboot
rpc_pipefs
rsync
rsyslog
saned
screen-cleanup
sendsigs
setserial
single
skeleton
speech-dispatcher
statd
statd-mounting
stop-bootlogd
stop-bootlogd-single
sudo
timidity
tomcat6
udev
udev-finish
udevmonitor
udevtrigger
ufw
umountfs
umountnfs.sh
umountroot
unattended-upgrades
urandom
x11-common

```

By the way, I have WebCit installed too and its script not in, "/etc/init.d" either?

How can I reinstall them or get the services recognized?

As they don't show in the list of services either:
```

$ service --status-all
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-mixer-save
 [ ? ]  anacron
 [ + ]  apache2
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ - ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ + ]  clamav-daemon
 [ + ]  clamav-freshclam
 [ ? ]  clamsmtp
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  etc-setserial
 [ ? ]  failsafe-x
 [ - ]  fancontrol
 [ - ]  grub-common
 [ ? ]  gssd
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  idmapd
 [ ? ]  irqbalance
 [ ? ]  kdm
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ ? ]  lirc
 [ - ]  lm-sensors
 [ + ]  memcached
 [ ? ]  module-init-tools
 [ ? ]  mysql
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  network-manager
 [ ? ]  networking
 [ + ]  nfs-kernel-server
 [ ? ]  ondemand
 [ ? ]  pcmciautils
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  portmap
 [ ? ]  portmap-boot
 [ ? ]  portmap-wait
 [ - ]  postfix
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ ? ]  rpc_pipefs
 [ - ]  rsync
 [ ? ]  rsyslog
 [ + ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ ? ]  setserial
 [ ? ]  speech-dispatcher
 [ ? ]  statd
 [ ? ]  statd-mounting
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  sudo
 [ + ]  timidity
 [ - ]  tomcat6
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ - ]  x11-common


```

---

### Post by HermanAB on 2011-04-29
Hi there,

How did you install Citadel, used the Ubuntu repos?

The Easy Install script from the [http://citadel.org](http://citadel.org) web site works every time, provided that your DNS and hostname are configured properly:
[http://www.aeronetworks.ca/howtos/citadel-basics.html](http://www.aeronetworks.ca/howtos/citadel-basics.html)

---

### Post by Horatio on 2011-04-29
Yes, I used aptitude and installed the citadel-suite.

---

### Post by Horatio on 2011-04-29
trying
```

$ sudo aptitude purge citadel-suite
[sudo] password for thann: 
The following packages will be REMOVED:  
  citadel-suite{p} citadel-webcit{u} libjs-prototype{u} libjs-scriptaculous{u} tinymce{u} 
0 packages upgraded, 0 newly installed, 5 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 6,779kB will be freed.
Do you want to continue? [Y/n/?] Y
(Reading database ... 257010 files and directories currently installed.)
Removing citadel-suite ...
(Reading database ... 257007 files and directories currently installed.)
Removing citadel-webcit ...
Removing libjs-scriptaculous ...
Removing libjs-prototype ...
Removing tinymce ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...

```
and
```

 sudo aptitude purge citadel-server
The following packages will be REMOVED:  
  citadel-server{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 2,462kB will be freed.
The following packages have unmet dependencies:
  citadel-mta: Depends: citadel-server (>= 7.50) but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:                      
1)     bsd-mailx                                         
2)     citadel-mta                                       
3)     mailutils                                         

     Leave the following dependencies unresolved:        
4)     mutt recommends default-mta | mail-transport-agent
5)     clamsmtp recommends postfix | mail-transport-agent


Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Remove the following packages:             
1)     citadel-mta                              

     Install the following packages:            
2)     lsb-invalid-mta [4.0-0ubuntu8 (maverick)]



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Remove the following packages: 
1)     citadel-mta                  

     Install the following packages:
2)     xmail [1.27-1 (maverick)]    



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Remove the following packages:      
1)     citadel-mta                       

     Install the following packages:     
2)     ssmtp [2.64-4fakesync1 (maverick)]



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Remove the following packages:      
1)     citadel-mta                       

     Install the following packages:     
2)     nullmailer [1:1.04-1.2 (maverick)]



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Remove the following packages:                                         
1)     citadel-mta                                                          

     Install the following packages:                                        
2)     postfix [2.7.1-1ubuntu0.1 (maverick-security, maverick-updates, now)]



Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  postfix{a} 
The following packages will be REMOVED:
  citadel-mta{a} citadel-server{p} 
0 packages upgraded, 1 newly installed, 2 to remove and 18 not upgraded.
Need to get 0B/1,389kB of archives. After unpacking 1,012kB will be used.
Do you want to continue? [Y/n/?] Y
Preconfiguring packages ...              
dpkg: citadel-mta: dependency problems, but removing anyway as you requested:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not installed.
  Package mail-transport-agent is not installed.
  Package citadel-mta which provides mail-transport-agent is to be removed.
  Package postfix which provides mail-transport-agent is not installed.
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is not installed.
  Package mail-transport-agent is not installed.
  Package citadel-mta which provides mail-transport-agent is to be removed.
  Package postfix which provides mail-transport-agent is not installed.
(Reading database ... 256209 files and directories currently installed.)
Removing citadel-mta ...
Processing triggers for man-db ...
(Reading database ... 256203 files and directories currently installed.)
Removing citadel-server ...
Purging configuration files for citadel-server ...
/var/lib/citadel/data not removed, as it may contain your personal data.
dpkg: warning: while removing citadel-server, directory '/var/lib/citadel/data' not empty so not removed.
dpkg: warning: while removing citadel-server, directory '/var/lib/citadel' not empty so not removed.
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Selecting previously deselected package postfix.
(Reading database ... 256139 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.7.1-1ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for man-db ...
Setting up postfix (2.7.1-1ubuntu0.1) ...
setting inet_protocols: ipv4

Postfix is now set up with the changes above.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix                                                                                                                               [ OK ] 
 * Starting Postfix Mail Transport Agent postfix                                                                                                                               [ OK ] 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Committing to: /etc/                                                                                                                                                                 
modified .etckeeper
modified aliases.db
missing citadel/mail.aliases
modified citadel/mail.aliases
missing citadel/messages
modified citadel/messages
missing citadel/netconfigs
modified citadel/netconfigs
missing citadel/public_clients
modified citadel/public_clients
missing citadel/messages/aideopt
modified citadel/messages/aideopt
missing citadel/messages/changepw
modified citadel/messages/changepw
missing citadel/messages/dotopt
modified citadel/messages/dotopt
missing citadel/messages/entermsg
modified citadel/messages/entermsg
missing citadel/messages/entopt
modified citadel/messages/entopt
missing citadel/messages/goodbye
modified citadel/messages/goodbye
missing citadel/messages/hello
modified citadel/messages/hello
missing citadel/messages/help
modified citadel/messages/help
missing citadel/messages/mainmenu
modified citadel/messages/mainmenu
missing citadel/messages/newuser
modified citadel/messages/newuser
missing citadel/messages/readopt
modified citadel/messages/readopt
missing citadel/messages/register
modified citadel/messages/register
missing citadel/messages/roomaccess
modified citadel/messages/roomaccess
missing citadel/messages/unlisted
modified citadel/messages/unlisted
missing citadel/netconfigs/7
modified citadel/netconfigs/7
added postfix/sasl
missing rc0.d/K20citadel                                                                                                                                                             
modified rc0.d/K20citadel
missing rc1.d/K20citadel
modified rc1.d/K20citadel
missing rc2.d/S20citadel
modified rc2.d/S20citadel
missing rc3.d/S20citadel
modified rc3.d/S20citadel
missing rc4.d/S20citadel
modified rc4.d/S20citadel
missing rc5.d/S20citadel
modified rc5.d/S20citadel
missing rc6.d/K20citadel
modified rc6.d/K20citadel
Committed revision 71.  

```
and then
```

$ sudo aptitude install citadel-suite
The following NEW packages will be installed:
  citadel-mta{ab} citadel-server{a} citadel-suite citadel-webcit{a} libjs-prototype{a} libjs-scriptaculous{a} tinymce{a} 
0 packages upgraded, 7 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B/1,751kB of archives. After unpacking 9,298kB will be used.
The following packages have unmet dependencies:
  postfix: Conflicts: mail-transport-agent which is a virtual package.
  citadel-mta: Conflicts: mail-transport-agent which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     postfix                     



Accept this solution? [Y/n/q/?] Y
The following NEW packages will be installed:
  citadel-mta{a} citadel-server{a} citadel-suite citadel-webcit{a} libjs-prototype{a} libjs-scriptaculous{a} tinymce{a} 
The following packages will be REMOVED:
  postfix{a} 
0 packages upgraded, 7 newly installed, 1 to remove and 18 not upgraded.
Need to get 0B/1,751kB of archives. After unpacking 5,767kB will be used.
Do you want to continue? [Y/n/?] Y
Committing to: /etc/                                                                                                                                                                 
modified cups/subscriptions.conf
modified cups/subscriptions.conf.O
Committed revision 72.                                                                                                                                                               
Preconfiguring packages ...
Selecting previously deselected package citadel-server.
(Reading database ... 256296 files and directories currently installed.)
Unpacking citadel-server (from .../citadel-server_7.72-3_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
dpkg: postfix: dependency problems, but removing anyway as you requested:
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.
 mailutils depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.
 bsd-mailx depends on default-mta | mail-transport-agent; however:
  Package default-mta is not installed.
  Package postfix which provides default-mta is to be removed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is to be removed.
(Reading database ... 256359 files and directories currently installed.)
Removing postfix ...
 * Stopping Postfix Mail Transport Agent postfix                                                                                                                               [ OK ] 
Processing triggers for man-db ...
Processing triggers for ufw ...
Processing triggers for ureadahead ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously deselected package citadel-mta.
(Reading database ... 256205 files and directories currently installed.)
Unpacking citadel-mta (from .../citadel-mta_7.72-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up citadel-server (7.72-3) ...
applying your settings.
postmaster,room_aide
Ignoring Alias postmaster as its already there
sendcommand: started (pid=26371) running in citadel
Attaching to server...
eisbrecher Citadel server ready.
Authenticated as an internal program.
DOWN
231 Shutting down server.  Goodbye.
sendcommand: processing ended.
Setting up citadel-mta (7.72-3) ...
Selecting previously deselected package libjs-prototype.
(Reading database ... 256211 files and directories currently installed.)
Unpacking libjs-prototype (from .../libjs-prototype_1.6.1-1_all.deb) ...
Selecting previously deselected package libjs-scriptaculous.
Unpacking libjs-scriptaculous (from .../libjs-scriptaculous_1.8.3-1_all.deb) ...
Selecting previously deselected package tinymce.
Unpacking tinymce (from .../tinymce_3.3.7-1_all.deb) ...
Selecting previously deselected package citadel-webcit.
Unpacking citadel-webcit (from .../citadel-webcit_7.72-dfsg-2_amd64.deb) ...
Selecting previously deselected package citadel-suite.
Unpacking citadel-suite (from .../citadel-suite_7.72-dfsg-2_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libjs-prototype (1.6.1-1) ...
Setting up libjs-scriptaculous (1.8.3-1) ...
Setting up tinymce (3.3.7-1) ...
Setting up citadel-webcit (7.72-dfsg-2) ...
Module proxy already enabled
Considering dependency proxy for proxy_http:
Module proxy already enabled
Module proxy_http already enabled
 * Reloading web server config apache2                                                                                                                                         [ OK ] 
Setting up citadel-suite (7.72-dfsg-2) ...
Committing to: /etc/                                                                                                                                                                 
modified .etckeeper
added citadel/mail.aliases
added citadel/messages
added citadel/netconfigs
added citadel/public_clients
added citadel/messages/aideopt
added citadel/messages/changepw
added citadel/messages/dotopt
added citadel/messages/entermsg
added citadel/messages/entopt
added citadel/messages/goodbye
added citadel/messages/hello
added citadel/messages/help
added citadel/messages/mainmenu
added citadel/messages/newuser
added citadel/messages/readopt
added citadel/messages/register
added citadel/messages/roomaccess
added citadel/messages/unlisted
added citadel/netconfigs/7
added init.d/citadel
missing postfix/sasl
modified postfix/sasl
added rc0.d/K20citadel
added rc1.d/K20citadel
added rc2.d/S20citadel
added rc3.d/S20citadel
added rc4.d/S20citadel
added rc5.d/S20citadel
added rc6.d/K20citadel
Committed revision 73.                                                                       

```
Now taking a peak with:
```

$ service --status-all
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-mixer-save
 [ ? ]  anacron
 [ + ]  apache2
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ - ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ ? ]  citadel
 [ + ]  clamav-daemon
 [ + ]  clamav-freshclam
 [ ? ]  clamsmtp
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  etc-setserial
 [ ? ]  failsafe-x
 [ - ]  fancontrol
 [ - ]  grub-common
 [ ? ]  gssd
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  idmapd
 [ ? ]  irqbalance
 [ ? ]  kdm
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ ? ]  lirc
 [ - ]  lm-sensors
 [ + ]  memcached
 [ ? ]  module-init-tools
 [ ? ]  mysql
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  network-manager
 [ ? ]  networking
 [ + ]  nfs-kernel-server
 [ ? ]  ondemand
 [ ? ]  pcmciautils
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  portmap
 [ ? ]  portmap-boot
 [ ? ]  portmap-wait
 [ - ]  postfix
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ ? ]  rpc_pipefs
 [ - ]  rsync
 [ ? ]  rsyslog
 [ + ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ ? ]  setserial
 [ ? ]  speech-dispatcher
 [ ? ]  statd
 [ ? ]  statd-mounting
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  sudo
 [ + ]  timidity
 [ - ]  tomcat6
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ - ]  x11-common

```
and
```

$ ls /etc/init.d | cat
acpid
acpi-support
alsa-mixer-save
anacron
apache2
apparmor
apport
atd
avahi-daemon
binfmt-support
bluetooth
bootlogd
brltty
citadel
clamav-daemon
clamav-freshclam
clamsmtp
console-setup
cron
cups
dbus
dmesg
dns-clean
etc-setserial
failsafe-x
fancontrol
grub-common
gssd
halt
hostname
hwclock
hwclock-save
idmapd
irqbalance
kdm
kerneloops
killprocs
lirc
lm-sensors
memcached
module-init-tools
mysql
networking
network-interface
network-interface-security
network-manager
nfs-kernel-server
ondemand
pcmciautils
plymouth
plymouth-log
plymouth-splash
plymouth-stop
portmap
portmap-boot
portmap-wait
postfix
pppd-dns
procps
pulseaudio
rc
rc.local
rcS
README
reboot
rpc_pipefs
rsync
rsyslog
saned
screen-cleanup
sendsigs
setserial
single
skeleton
speech-dispatcher
statd
statd-mounting
stop-bootlogd
stop-bootlogd-single
sudo
timidity
tomcat6
udev
udev-finish
udevmonitor
udevtrigger
ufw
umountfs
umountnfs.sh
umountroot
unattended-upgrades
urandom
x11-common

```
Oh what, webcit is still missing?! mjoelk!
```

$ sudo aptitude purge citadelwebcit
Couldn't find any package whose name or description matched "citadelwebcit"
Couldn't find any package whose name or description matched "citadelwebcit"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
                                         
thann@eisbrecher:/etc/init.d$ sudo aptitude purge citadel-webcit
The following packages will be REMOVED:  
  citadel-webcit{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 3,113kB will be freed.
The following packages have unmet dependencies:
  citadel-suite: Depends: citadel-webcit but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     citadel-suite               



Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  citadel-suite{a} citadel-webcit{p} libjs-prototype{u} libjs-scriptaculous{u} tinymce{u} 
0 packages upgraded, 0 newly installed, 5 to remove and 18 not upgraded.
Need to get 0B of archives. After unpacking 6,779kB will be freed.
Do you want to continue? [Y/n/?] Y
(Reading database ... 257010 files and directories currently installed.)
Removing citadel-suite ...
(Reading database ... 257007 files and directories currently installed.)
Removing citadel-webcit ...
Purging configuration files for citadel-webcit ...
/etc/citadel/www/keys not removed. 
 * Reloading web server config apache2                                                                                                                                         [ OK ] 
Processing triggers for ureadahead ...
Processing triggers for man-db ...
(Reading database ... 256673 files and directories currently installed.)
Removing libjs-scriptaculous ...
Removing libjs-prototype ...
Removing tinymce ...
Committing to: /etc/                                                                                                                                                                 
modified .etckeeper
missing apache2/conf.d/webcit.conf
modified apache2/conf.d/webcit.conf
missing citadel/webcit.conf
modified citadel/webcit.conf
missing default/webcit
modified default/webcit
missing rc0.d/K20webcit
modified rc0.d/K20webcit
missing rc1.d/K20webcit
modified rc1.d/K20webcit
missing rc2.d/S20webcit
modified rc2.d/S20webcit
missing rc3.d/S20webcit
modified rc3.d/S20webcit
missing rc4.d/S20webcit
modified rc4.d/S20webcit
missing rc5.d/S20webcit
modified rc5.d/S20webcit
missing rc6.d/K20webcit
modified rc6.d/K20webcit
Committed revision 74.

```
Then install again and they both now appear.
```

$ service --status-all
 [ ? ]  acpi-support
 [ ? ]  acpid
 [ ? ]  alsa-mixer-save
 [ ? ]  anacron
 [ + ]  apache2
 [ - ]  apparmor
 [ ? ]  apport
 [ ? ]  atd
 [ ? ]  avahi-daemon
 [ ? ]  binfmt-support
 [ - ]  bluetooth
 [ - ]  bootlogd
 [ - ]  brltty
 [ ? ]  citadel
 [ + ]  clamav-daemon
 [ + ]  clamav-freshclam
 [ ? ]  clamsmtp
 [ ? ]  console-setup
 [ ? ]  cron
 [ ? ]  cups
 [ ? ]  dbus
 [ ? ]  dmesg
 [ ? ]  dns-clean
 [ ? ]  etc-setserial
 [ ? ]  failsafe-x
 [ - ]  fancontrol
 [ - ]  grub-common
 [ ? ]  gssd
 [ ? ]  hostname
 [ ? ]  hwclock
 [ ? ]  hwclock-save
 [ ? ]  idmapd
 [ ? ]  irqbalance
 [ ? ]  kdm
 [ - ]  kerneloops
 [ ? ]  killprocs
 [ ? ]  lirc
 [ - ]  lm-sensors
 [ + ]  memcached
 [ ? ]  module-init-tools
 [ ? ]  mysql
 [ ? ]  network-interface
 [ ? ]  network-interface-security
 [ ? ]  network-manager
 [ ? ]  networking
 [ + ]  nfs-kernel-server
 [ ? ]  ondemand
 [ ? ]  pcmciautils
 [ ? ]  plymouth
 [ ? ]  plymouth-log
 [ ? ]  plymouth-splash
 [ ? ]  plymouth-stop
 [ ? ]  portmap
 [ ? ]  portmap-boot
 [ ? ]  portmap-wait
 [ - ]  postfix
 [ ? ]  pppd-dns
 [ ? ]  procps
 [ + ]  pulseaudio
 [ ? ]  rc.local
 [ ? ]  rpc_pipefs
 [ - ]  rsync
 [ ? ]  rsyslog
 [ + ]  saned
 [ ? ]  screen-cleanup
 [ ? ]  sendsigs
 [ ? ]  setserial
 [ ? ]  speech-dispatcher
 [ ? ]  statd
 [ ? ]  statd-mounting
 [ ? ]  stop-bootlogd
 [ ? ]  stop-bootlogd-single
 [ ? ]  sudo
 [ + ]  timidity
 [ - ]  tomcat6
 [ ? ]  udev
 [ ? ]  udev-finish
 [ ? ]  udevmonitor
 [ ? ]  udevtrigger
 [ ? ]  ufw
 [ ? ]  umountfs
 [ ? ]  umountnfs.sh
 [ ? ]  umountroot
 [ ? ]  unattended-upgrades
 [ - ]  urandom
 [ ? ]  webcit
 [ - ]  x11-common

```

---

### Post by Horatio on 2011-04-29
So I added a virtual host configuration as [http://www.citadel.org/doku.php/faq:installation:apacheproxy#how.can.i.install.webcit.so.it.runs.alongside.apache.nginx.on.port.80.443]("http://www.citadel.org/doku.php/faq:installation:apacheproxy#how.can.i.install.webcit.so.it.runs.alongside.apache.nginx.on.port.80.443") suggests, and I reloaded apache2. 

Well, WebCit seems to be working. Thanks!

---

