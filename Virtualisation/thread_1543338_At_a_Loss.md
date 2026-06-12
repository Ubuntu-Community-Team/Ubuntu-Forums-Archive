---
title: "At a Loss"
date: 2010-07-31
forum: Virtualisation
---

### Post by diablo69er on 2010-07-31
So I installed vmware workstation from the bundle file from vmware website to test it out.  Turns out it's not what I really want, and I have no idea how to do uninstall it.

Now before you show me links about Google it search the forums etc..I did.  Nothing that was recommended to me worked thus far.

I have looked for the vmware-uninstall.pl file in /usr/bin.

ran perl vmware-uninstall.pl (nothing happened)
I followed the steps exactly on how to manually remove it (was looking for the link again on vmware's site but didn't see it)

i've also done find / -name vmware

did a rm -rf on everything that showed up..

--edit So I grabbed the .bundle file from vmware again tried to reinstall it, but I couldn't.  It says it's already intalled..which is clearly not the case because I manually removed everything..

any ideas?

---

### Post by HermanAB on 2010-08-01
Howdy,

You are on the right track.  Just delete it and stop the service.  

The service is strated with a script from somewhere in /etc.  Find it and delete it.  

You can see what is running with:
$ sudo ps -e

Then simply do:
$ sudo kill -9 PID

---

### Post by diablo69er on 2010-08-01
Hey HermanAB,

TY for the reply, i did just that, and saw a good portion of processes, but none are even close to vmware..any other idea's?

I'll paste the output for kicks

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:01 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:00 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:00 events/0
   16 ?        00:00:00 events/1
   17 ?        00:00:00 events/2
   18 ?        00:00:00 events/3
   19 ?        00:00:00 cpuset
   20 ?        00:00:00 khelper
   21 ?        00:00:00 netns
   22 ?        00:00:00 async/mgr
   23 ?        00:00:00 pm
   25 ?        00:00:00 sync_supers
   26 ?        00:05:19 bdi-default
   27 ?        00:00:00 kintegrityd/0
   28 ?        00:00:00 kintegrityd/1
   29 ?        00:00:00 kintegrityd/2
   30 ?        00:00:00 kintegrityd/3
   31 ?        00:00:00 kblockd/0
   32 ?        00:00:00 kblockd/1
   33 ?        00:00:01 kblockd/2
   34 ?        00:00:00 kblockd/3
   35 ?        00:00:00 kacpid
   36 ?        00:00:00 kacpi_notify
   37 ?        00:00:00 kacpi_hotplug
   38 ?        00:00:00 ata/0
   39 ?        00:00:07 ata/1
   40 ?        00:00:00 ata/2
   41 ?        00:00:00 ata/3
   42 ?        00:00:00 ata_aux
   43 ?        00:00:00 ksuspend_usbd
   44 ?        00:00:00 khubd
   45 ?        00:00:00 kseriod
   46 ?        00:00:00 kmmcd
   51 ?        00:00:00 khungtaskd
   52 ?        00:00:36 kswapd0
   53 ?        00:00:00 ksmd
   54 ?        00:00:00 aio/0
   55 ?        00:00:00 aio/1
   56 ?        00:00:00 aio/2
   57 ?        00:00:00 aio/3
   58 ?        00:00:00 ecryptfs-kthrea
   59 ?        00:00:00 crypto/0
   60 ?        00:00:00 crypto/1
   61 ?        00:00:00 crypto/2
   62 ?        00:00:00 crypto/3
   66 ?        00:00:00 kstriped
   67 ?        00:00:00 kmpathd/0
   68 ?        00:00:00 kmpathd/1
   69 ?        00:00:00 kmpathd/2
   70 ?        00:00:00 kmpathd/3
   71 ?        00:00:00 kmpath_handlerd
   72 ?        00:00:00 ksnapd
   73 ?        00:00:00 kondemand/0
   74 ?        00:00:00 kondemand/1
   75 ?        00:00:00 kondemand/2
   76 ?        00:00:00 kondemand/3
   77 ?        00:00:00 kconservative/0
   78 ?        00:00:00 kconservative/1
   79 ?        00:00:00 kconservative/2
   80 ?        00:00:00 kconservative/3
  217 ?        00:00:00 scsi_eh_0
  275 ?        00:00:00 scsi_eh_1
  291 ?        00:00:00 scsi_eh_2
  300 ?        00:00:00 scsi_eh_3
  324 ?        00:00:00 khpsbpkt
  325 ?        00:00:00 scsi_eh_4
  326 ?        00:00:00 scsi_eh_5
  328 ?        00:00:00 scsi_eh_6
  330 ?        00:00:00 scsi_eh_7
  333 ?        00:00:00 scsi_eh_8
  334 ?        00:00:00 scsi_eh_9
  336 ?        00:00:00 scsi_eh_10
  337 ?        00:00:00 scsi_eh_11
  341 ?        00:00:00 scsi_eh_12
  342 ?        00:00:00 scsi_eh_13
  345 ?        00:00:00 scsi_eh_14
  346 ?        00:00:09 scsi_eh_15
  366 ?        00:00:00 usbhid_resumer
  372 ?        00:00:00 knodemgrd_0
  484 ?        00:00:03 kdmflush
  485 ?        00:00:19 kcryptd_io
  486 ?        00:28:40 kcryptd
  502 ?        00:00:00 kdmflush
  505 ?        00:00:00 kdmflush
  519 ?        00:00:42 flush-252:1
  532 ?        00:00:06 jbd2/dm-1-8
  533 ?        00:00:00 ext4-dio-unwrit
  534 ?        00:00:00 ext4-dio-unwrit
  535 ?        00:00:00 ext4-dio-unwrit
  536 ?        00:00:00 ext4-dio-unwrit
  578 ?        00:00:00 upstart-udev-br
  581 ?        00:00:00 udevd
 1037 ?        00:00:00 hd-audio2
 1118 ?        00:00:00 rsyslogd
 1157 ?        00:00:01 dbus-daemon
 1163 ?        00:00:00 gdm-binary
 1168 ?        00:00:00 avahi-daemon
 1169 ?        00:00:00 NetworkManager
 1170 ?        00:00:00 avahi-daemon
 1172 ?        00:00:00 modem-manager
 1184 ?        00:00:00 wpa_supplicant
 1186 ?        00:00:00 dhclient
 1208 tty4     00:00:00 getty
 1212 tty5     00:00:00 getty
 1219 tty2     00:00:00 getty
 1220 tty3     00:00:00 getty
 1222 tty6     00:00:00 getty
 1225 ?        00:00:00 acpid
 1237 ?        00:00:01 irqbalance
 1251 ?        00:00:00 atd
 1252 ?        00:00:00 cron
 1569 ?        00:00:00 exim4
 1574 ?        00:00:00 console-kit-dae
 1691 ?        00:00:00 winbindd
 1721 ?        00:00:00 kdmflush
 1725 ?        00:00:00 kcryptd_io
 1726 ?        00:00:00 kcryptd
 1746 ?        00:00:00 winbindd
 1829 ?        00:00:00 apache2
 1833 ?        00:00:00 apache2
 1834 ?        00:00:00 apache2
 1835 ?        00:00:00 apache2
 1836 ?        00:00:00 apache2
 1838 ?        00:00:00 apache2
 1897 tty1     00:00:00 getty
 1949 ?        00:00:00 upowerd
 1959 ?        00:00:00 polkitd
 1985 ?        00:00:00 hald
 1986 ?        00:00:00 hald-runner
 2011 ?        00:00:01 hald-addon-inpu
 2025 ?        00:00:15 hald-addon-stor
 2027 ?        00:00:00 hald-addon-acpi
 2145 ?        00:11:13 pulseaudio
 2147 ?        00:00:00 rtkit-daemon
 2215 ?        00:00:00 gconf-helper
 2230 ?        00:00:02 udisks-daemon
 2233 ?        00:00:05 udisks-daemon
 2343 ?        00:00:00 gnome-terminal
 2346 ?        00:00:00 gnome-pty-helpe
 2347 pts/0    00:00:00 bash
 2353 ?        00:00:00 evolution-data-
 2412 pts/0    00:00:00 ps
 2495 ?        00:00:00 system-service-
 4591 ?        00:15:00 plugin-containe
 7482 ?        00:04:46 mount.ntfs
 7806 ?        00:00:00 udevd
 9699 ?        00:00:00 cupsd
10450 ?        00:00:00 gvfsd-computer
12089 ?        00:00:00 gvfsd-metadata
13284 ?        00:00:00 udevd
16088 ?        00:00:04 python
22262 ?        00:00:28 pidgin
24135 ?        00:00:00 gdm-simple-slav
24137 tty8     00:25:18 Xorg
24157 ?        00:00:00 dbus-launch
24175 ?        00:00:00 gdm-session-wor
24187 ?        00:00:00 gnome-keyring-d
24205 ?        00:00:00 gnome-session
24239 ?        00:00:00 ssh-agent
24242 ?        00:00:00 dbus-launch
24243 ?        00:00:05 dbus-daemon
24246 ?        00:00:06 gconfd-2
24253 ?        00:00:23 gnome-settings-
24255 ?        00:00:00 gvfsd
24260 ?        00:00:00 bluetooth-apple
24267 ?        00:00:09 gnome-panel
24268 ?        00:01:48 nautilus
24269 ?        00:00:01 alltray
24271 ?        00:00:00 fusion-icon
24273 ?        00:00:00 polkit-gnome-au
24274 ?        00:00:00 gnome-power-man
24275 ?        00:00:00 nm-applet
24305 ?        00:00:00 gvfs-gdu-volume
24326 ?        00:00:00 gvfs-gphoto2-vo
24329 ?        00:00:00 gvfs-afc-volume
24332 ?        00:00:00 gvfsd-trash
24334 ?        00:00:00 bonobo-activati
24349 ?        00:00:00 gvfs-fuse-daemo
24358 ?        00:00:00 gvfsd-burn
24369 ?        00:01:07 wnck-applet
24370 ?        00:00:00 trashapplet
24377 ?        00:00:00 gweather-applet
24378 ?        00:00:01 indicator-apple
24381 ?        00:00:02 notification-ar
24382 ?        00:00:01 clock-applet
24383 ?        00:05:40 compiz
24405 ?        00:00:00 sh
24406 ?        00:01:10 emerald
24408 ?        00:00:00 thunderbird
24413 ?        00:00:00 run-mozilla.sh
24417 ?        00:05:08 thunderbird-bin
24421 ?        00:00:00 indicator-sessi
24423 ?        00:00:00 indicator-me-se
24432 ?        00:00:01 gnome-screensav
24434 ?        00:00:00 zeitgeist-daemo
24443 ?        00:00:10 zeitgeist-datah
24447 ?        00:00:04 notify-osd
24457 ?        00:00:44 python
24478 ?        00:00:00 gdu-notificatio
24525 ?        00:00:04 python
24526 ?        00:00:00 evolution-alarm
24531 ?        00:00:00 evolution-excha
24535 ?        00:00:00 evolution-data-
24621 ?        00:00:01 update-notifier
25003 ?        00:00:00 gvfsd-archive
25478 ?        00:00:00 skype-wrapper
25479 ?        00:11:49 skype
28370 ?        00:00:00 firefox
28375 ?        00:00:00 run-mozilla.sh
28379 ?        00:17:27 firefox-bin
28614 ?        00:02:45 rhythmbox
30752 ?        00:01:18 xchat
32299 ?        00:00:00 gvfsd-http

---

### Post by HermanAB on 2010-08-03
If there is no vmware process, then it is not running.

You can search the process list with something like:
$ sudo ps -e | grep vm*

---

