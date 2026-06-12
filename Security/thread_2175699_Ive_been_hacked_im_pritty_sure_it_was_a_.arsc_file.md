---
title: "Ive been hacked im pritty sure it was a .arsc file that got me"
date: 2013-09-20
forum: Security
---

### Post by jdog1907 on 2013-09-20
so ive done aboght every thing i can think of i need orofesional help when i get close to fixing the problem the hacker or hackers in my system stop me i dont know what to do

---

### Post by QIII on 2013-09-20
Hello!

You have one other post, a hijack of another thread, and your problem is not described well there.

Could you give everyone something to work from by describing your symptoms here?

---

### Post by deadflowr on 2013-09-20
Adding to what QIII asked, it would also be helpful to know what you've thus far tried to do.
Or thought of doing.

---

### Post by jdog1907 on 2013-09-20
i have a bunch of programs i did not download on my laptop when i tryed to instal bit defender i was prevented from doing so by someone when i try to download something it goes at a snales pace nothing i do causes my harddrive to spin up to fullspeed transfering files downloading nothing and my root files are locked but i didnot lock them im pritty sure i have a virus i cant detect it but im being hacked to there are files in my recent accessed box i did not access and cant deliete. my hard drive kicks up to full speed at odd times when im not really doing anything to cause it when i look at the cpu meter it will show more activity but when i go in to see what programs are runing there wont be anything that is active on it except the gnome system monitor. i tried to remove some programs that i had not put on my pc and was able to take off a cople then it stalled out abought half way threw the 3rd and the next day they were all back like i never delieted anything. i change settings only to later find them back were they started at. setings will be locked when i unlock them the lock disapears like there never was one. that is just some of the stuff that has happened plus on my network tools there is alott of activity i have changed harddrives that fixed my problems untill i hooked my phone to my pc trying to get online with it and it did intermitantly for a few min then it came up with an error the phone reinfected it with the virus and the virus allows the hacker access i think. when i was useing win 7 i could see when someone got on because there the screen would have interferance jaged lines that would run across it and there was a hole series of events while i was useing win 7 i dont even want to get into all of those events i change to unibutu 13.4 hoping that who ever is messing with me would not know linix no such luck i think they know this operating sistem even better but it is easyer to detect them i just dont know how to get rid of someone allready in your sistem when they block u when u get clos to kicking them off im not fast enough and dont know the comands i need help

---

### Post by vasa1 on 2013-09-20
I'm wondering about this thread.

---

### Post by cariboo on 2013-09-20
Do you get any of these problems when running from a live CD or USB?

---

### Post by claracc on 2013-09-21
> **vasa1 said:**
> I'm wondering about this thread.

Me too.  As we say in spain (tied to translate to english language), it seems a "story for not to sleep" ( in short, a scary movie).

---

### Post by unspawn on 2013-09-21
First of all please use proper punctuation: makes it easier to read. 

Secondly, as goes with the other recent "help I've got a virus" thread: do not automagically assume that, because of your experiences with Lesser Operating Systems, that you've contracted a virus and *if* you remain adamant you did contract one then post actual output from running checks and scans. Do not say:
> **jdog1907 said:**
> i have a bunch of programs i did not download on my laptop 
but actually list them Do not say:
> **jdog1907 said:**
> when i try to download something it goes at a snales pace 
but actually list the URI (or whatever "snales pace" means). Do not say:
> **jdog1907 said:**
> nothing i do causes my harddrive to spin up to fullspeed
but run (as root) ```
iostat
``` and
```
N=0.1; /bin/ps --no-headers axkpcpu -o pcpu,pid,args | awk -v N=$1 '{ if ($1 > N) print }';
```Do not say:
> **jdog1907 said:**
> there are files in my recent accessed box i did not access and cant deliete. 
but actually list them running ```
/bin/ls --color=never --full-time --time-style=long-iso --quoting-style=c -1 -U /path/to/wherever/"accessed box"/is
```
Do not say:
> **jdog1907 said:**
> i change settings only to later find them back were they started at. 
but tell us what settings you're actually changing.

Finally > **jdog1907 said:**
> i need help most of this awfully sounds like a user new to Linux not knowing how Linux works (with all due respect) so I suggest you start with basic Ubuntu documentation to understand of how things are done "the Linux way" (ownership, permissions) and how things are done with your particular distribution. Note that if you thing I'm wrong (which may well be the case) then correct me *posting only actual data and information, not stories*.

---

### Post by jdog1907 on 2013-09-22
thank u for ure help i should have been posting. as i did what i could and been geting help. i was trying to fix my problem by my self. i really dont like to have to ask for help. i am now at the realization i cant fix tis on my own. so my origional post was a generalization of some of the stuff i have noticed.

---

### Post by jdog1907 on 2013-09-22
so this is what i got when i used the first two codes u told me i could use 

```
The program 'iostat' is currently not installed. You can install it by typing:
apt-get install sysstat
root@jdog1907-Inspiron-15455:/home/jdog1907# apt-get install sysstat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dockmanager kde-l10n-engb libgnome-desktop-2-17 libgnomedesktop2.20-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-services4.0-cil libmono-system-web4.0-cil
  libmono-system-xml-linq4.0-cil libmono-web4.0-cil libnotify0.4-cil
  librsvg2-2.18-cil libwnck2.20-cil python-mpd python-mutagen
Use 'apt-get autoremove' to remove them.
Suggested packages:
  isag
The following NEW packages will be installed:
  sysstat
0 upgraded, 1 newly installed, 0 to remove and 61 not upgraded.
1 not fully installed or removed.
Need to get 307 kB of archives.
After this operation, 942 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring/main sysstat amd64 10.0.5-1 [307 kB]
Fetched 307 kB in 2s (129 kB/s)   
Preconfiguring packages ...
Selecting previously unselected package sysstat.
(Reading database ... 282051 files and directories currently installed.)
Unpacking sysstat (from .../sysstat_10.0.5-1_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up samba4 (4.0.0+dfsg1-1ubuntu1) ...
ERROR(<type 'exceptions.ValueError'>): uncaught exception - unable to parse dn string
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/__init__.py", line 175, in _run
    return self.run(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/samba/netcmd/dbcheck.py", line 108, in run
    fix=fix, yes=yes, quiet=quiet, in_transaction=started_transaction)
  File "/usr/lib/python2.7/dist-packages/samba/dbchecker.py", line 56, in __init__
    self.infrastructure_dn = ldb.Dn(samdb, "CN=Infrastructure," + samdb.domain_dn())
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up sysstat (10.0.5-1) ...

Creating config file /etc/default/sysstat with new version
update-alternatives: using /usr/bin/sar.sysstat to provide /usr/bin/sar (sar) in auto mode
Processing triggers for ureadahead ...
Errors were encountered while processing:
 samba4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
root@jdog1907-Inspiron-15455:/home/jdog1907# N=0.1; /bin/ps --no-headers axkpcpu -o pcpu,pid,args | awk -v N=$1 '{ if ($1 > N) print }';
 0.0     1 /sbin/init
 0.0     2 [kthreadd]
 0.0     3 [ksoftirqd/0]
 0.0     5 [kworker/0:0H]
 0.0     7 [kworker/u:0H]
 0.0     8 [migration/0]
 0.0     9 [rcu_bh]
 0.0    10 [rcu_sched]
 0.0    11 [watchdog/0]
 0.0    12 [watchdog/1]
 0.0    13 [ksoftirqd/1]
 0.0    14 [migration/1]
 0.0    16 [kworker/1:0H]
 0.0    17 [cpuset]
 0.0    18 [khelper]
 0.0    19 [kdevtmpfs]
 0.0    20 [netns]
 0.0    21 [bdi-default]
 0.0    22 [kintegrityd]
 0.0    23 [kblockd]
 0.0    24 [ata_sff]
 0.0    25 [khubd]
 0.0    26 [md]
 0.0    27 [devfreq_wq]
 0.0    30 [khungtaskd]
 0.0    31 [kswapd0]
 0.0    32 [ksmd]
 0.0    33 [khugepaged]
 0.0    34 [fsnotify_mark]
 0.0    35 [ecryptfs-kthrea]
 0.0    36 [crypto]
 0.0    47 [kthrotld]
 0.0    50 [scsi_eh_0]
 0.0    51 [scsi_eh_1]
 0.0    53 [scsi_eh_2]
 0.0    54 [scsi_eh_3]
 0.0    55 [kworker/u:3]
 0.0    57 [binder]
 0.0    58 [kworker/u:5]
 0.0    77 [deferwq]
 0.0    78 [charger_manager]
 0.0   325 [kdmflush]
 0.0   327 [kcryptd_io]
 0.0   328 [kcryptd]
 0.0   340 [kdmflush]
 0.0   342 [kdmflush]
 0.0   362 [kworker/1:1H]
 0.0   363 [kworker/0:1H]
 0.0   364 [jbd2/dm-1-8]
 0.0   365 [ext4-dio-unwrit]
 0.0   388 [flush-252:1]
 0.0   391 mountall --daemon
 0.0   434 upstart-file-bridge --daemon
 0.0   502 upstart-udev-bridge --daemon
 0.0   506 /sbin/udevd --daemon
 0.0   559 [cfg80211]
 0.0   596 [wl_event_handle]
 0.0   622 [hd-audio0]
 0.0   655 /sbin/udevd --daemon
 0.0   656 /sbin/udevd --daemon
 0.0   669 [kpsmoused]
 0.0   936 upstart-socket-bridge --daemon
 0.0  1089 dbus-daemon --system --fork
 0.0  1096 rsyslogd -c5
 0.0  1110 /usr/sbin/modem-manager
 0.0  1155 /usr/sbin/bluetoothd
 0.0  1170 [krfcommd]
 0.0  1195 /sbin/getty -8 38400 tty4
 0.0  1199 /sbin/getty -8 38400 tty5
 0.0  1205 /sbin/getty -8 38400 tty2
 0.0  1206 /sbin/getty -8 38400 tty3
 0.0  1208 /sbin/getty -8 38400 tty6
 0.0  1233 acpid -c /etc/acpi/events -s /var/run/acpid.socket
 0.0  1236 gdm
 0.0  1318 avahi-daemon: running [jdog1907-Inspiron-15455.local]
 0.0  1324 avahi-daemon: chroot helper
 0.0  1337 /usr/sbin/cups-browsed
 0.0  1355 cron
 0.0  1356 /usr/sbin/named -u bind
 0.0  1379 /usr/sbin/cupsd -F
 0.0  1382 NetworkManager
 0.0  1385 /usr/lib/gdm/gdm-simple-slave --display-id /org/gnome/DisplayManager/Displays/_0
 0.0  1390 /usr/lib/policykit-1/polkitd --no-debug
 0.0  1520 /sbin/wpa_supplicant -B -P /run/sendsigs.omit.d/wpasupplicant.pid -u -s -O /var/run/wpa_supplicant
 0.0  1655 /usr/sbin/libvirtd -d
 0.0  1681 /usr/sbin/exim4 -bd -q30m
 0.0  1715 whoopsie
 0.0  1739 samba -D
 0.0  1744 samba -D
 0.0  1745 samba -D
 0.0  1746 samba -D
 0.0  1748 samba -D
 0.0  1753 samba -D
 0.0  1755 samba -D
 0.0  1766 nginx: master process /usr/sbin/nginx
 0.0  1767 nginx: worker process
 0.0  1768 nginx: worker process
 0.0  1769 nginx: worker process
 0.0  1770 nginx: worker process
 0.0  1783 /usr/sbin/popa3d -D
 0.0  1823 /sbin/dhclient -d -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /run/sendsigs.omit.d/network-manager.dhclient-eth1.pid -lf /var/lib/NetworkManager/dhclient-b7ba26a9-5bff-4e7a-b917-fab85140be08-eth1.lease -cf /var/lib/NetworkManager/dhclient-eth1.conf eth1
 0.0  2011 /sbin/getty -8 38400 tty1
 0.0  2016 /usr/lib/accountsservice/accounts-daemon
 0.0  2100 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf
 0.0  2104 /usr/sbin/console-kit-daemon --no-daemon
 0.0  2213 [kauditd]
 0.0  2274 [kdmflush]
 0.0  2281 [kcryptd_io]
 0.0  2282 [kcryptd]
 0.0  2294 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --conf-file=/var/run/NetworkManager/dnsmasq.conf --cache-size=0 --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
 0.0  2444 /usr/sbin/winbindd -F
 0.0  2469 /usr/sbin/winbindd -F
 0.0  2514 /usr/lib/upower/upowerd
 0.0  2690 /usr/lib/rtkit/rtkit-daemon
 0.0  2703 /usr/lib/udisks2/udisksd --no-debug
 0.0  2756 gdm-session-worker [pam/gdm-password]
 0.0  2802 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 122:131
 0.0  2822 /usr/bin/gnome-keyring-daemon --daemonize --login
 0.0  2841 gnome-session --session=gnome
 0.0  2898 dbus-launch --autolaunch=4af48d46f76e135f51624900522939a9 --binary-syntax --close-stderr
 0.0  2900 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 0.0  2901 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-session --session=gnome
 0.0  2904 /usr/bin/dbus-launch --exit-with-session /usr/bin/im-launch gnome-session --session=gnome
 0.0  2905 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 0.0  2915 /usr/lib/at-spi2-core/at-spi-bus-launcher
 0.0  2919 /bin/dbus-daemon --config-file=/etc/at-spi2/accessibility.conf --nofork --print-address 3
 0.0  2922 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
 0.0  2937 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 0.0  2943 /usr/bin/pulseaudio --start --log-target=syslog
 0.0  2949 /usr/lib/gvfs/gvfsd
 0.0  2953 /usr/lib/gvfs//gvfsd-fuse -f /run/user/jdog1907/gvfs
 0.0  2967 /usr/lib/colord/colord
 0.0  2981 /usr/lib/gnome-settings-daemon/gsd-locate-pointer
 0.0  2989 syndaemon -i 1.0 -t -K -R
 0.0  3001 nm-applet
 0.0  3002 /usr/lib/tracker/tracker-store
 0.0  3003 /usr/lib/tracker/tracker-miner-fs
 0.0  3005 nautilus -n
 0.0  3016 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
 0.0  3022 /usr/lib/gvfs/gvfs-udisks2-volume-monitor
 0.0  3026 /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
 0.0  3032 /usr/lib/gvfs/gvfs-mtp-volume-monitor
 0.0  3036 /usr/lib/gvfs/gvfs-afc-volume-monitor
 0.0  3044 [flush-ecryptfs-]
 0.0  3047 /usr/lib/gnome-shell/gnome-shell-calendar-server
 0.0  3053 /usr/lib/evolution/evolution-source-registry
 0.0  3059 /usr/lib/gvfs/gvfsd-trash --spawner :1.8 /org/gtk/gvfs/exec_spaw/0
 0.0  3067 /usr/lib/gvfs/gvfsd-burn --spawner :1.8 /org/gtk/gvfs/exec_spaw/1
 0.0  3074 /usr/lib/gnome-online-accounts/goa-daemon
 0.0  3076 /usr/lib/evolution/evolution-calendar-factory
 0.0  3078 /usr/lib/telepathy/mission-control-5
 0.0  3093 /usr/lib/gvfs/gvfsd-metadata
 0.0  3111 zeitgeist-datahub
 0.0  3117 /usr/bin/zeitgeist-daemon
 0.0  3124 /usr/lib/zeitgeist/zeitgeist-fts
 0.0  3180 /bin/cat
 0.0  3204 /usr/lib/evolution/evolution-addressbook-factory
 0.0  3231 /usr/lib/evolution/3.6/evolution-alarm-notify
 0.0  3246 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
 0.0  3305 /usr/lib/libunity-webapps/unity-webapps-service
 0.0  3366 update-notifier
 0.0  3400 /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
 0.0  3426 deja-dup --backup --auto
 0.0  3626 /usr/lib/dconf/dconf-service
 0.0  3975 [kworker/1:1]
 0.0  4011 [kworker/1:0]
 0.0  4012 [kworker/0:2]
 0.0  4169 /usr/bin/sudo -H -S -p GNOME_SUDO_PASS -u root -- /usr/bin/x-terminal-emulator
 0.0  4175 dbus-launch --autolaunch=4af48d46f76e135f51624900522939a9 --binary-syntax --close-stderr
 0.0  4176 //bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
 0.0  4182 /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
 0.0  4184 gnome-pty-helper
 0.0  4185 bash
 0.0  4937 /usr/lib/packagekit/packagekitd
 0.0  5054 [kworker/0:0]
 0.0  5708 /bin/ps --no-headers axkpcpu -o pcpu,pid,args
 0.0  5709 awk -v N= { if ($1 > N) print }
 0.1  4141 [kworker/0:1]
 0.1  4165 gksu /usr/bin/x-terminal-emulator
 0.2  4155 [kworker/1:2]
 0.4  4171 gnome-terminal
 1.4  1689 /usr/bin/X :0 -background none -verbose -auth /run/gdm/auth-for-gdm-roIEWf/database -nolisten tcp vt7
 2.7  2995 /usr/bin/gnome-shell
 3.4  4945 /usr/bin/python3 /usr/share/apport/apport-gtk
 4.7  3288 /usr/lib/firefox/firefox
```

---

### Post by jdog1907 on 2013-09-22
i dont have a amd64

---

### Post by cariboo on 2013-09-22
The only thing I can see is a problem installing samba4. I'd suggest using synaptic package manager to remove the broken samba4 package, then try again.

---

### Post by vasa1 on 2013-09-22
Another thing: looks like OP is using root rather than sudo:
```
root@jdog1907-Inspiron-15455:/home/jdog1907# apt-get install sysstat
```

---

### Post by cariboo on 2013-09-23
> **jdog1907 said:**
> i dont have a amd64

You have to have a 64-bit cpu in order to install 64-bit packages, even if you are running an intel cpu, you will get amd64 packages, it's just a naming convention.

---

