---
title: "can't install anything"
date: 2005-08-09
forum: Repositories &amp; Backports
---

### Post by kramer3d on 2005-08-09
when ever i try to install anything, i get this error
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
``` 

Also if I try to run synaptic, I get this message: You must run this as root user.

---

### Post by mato on 2005-08-09
Run synaptic as root user

in command line type:

sudo synaptic

When prompted, type your user password.

---

### Post by blind0wl on 2005-08-09
How are you trying to apt-get?  Through synaptic or console...that statement is saying something all ready has the package management system open somewhere.  Only one app can run it at a time, so if your trying to console apt-get and synaptic, you'll get that error message...if your not, it might be a rogue process in the background....post the output of: ```
ps -A
``` or reboot should fix it if your lazy  :razz:

---

### Post by kramer3d on 2005-08-23
```
  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 ksoftirqd/0
    3 ?        00:00:00 events/0
    4 ?        00:00:00 khelper
   22 ?        00:00:00 kacpid
  101 ?        00:00:00 kblockd/0
  139 ?        00:00:00 pdflush
  140 ?        00:00:00 pdflush
  142 ?        00:00:00 aio/0
  141 ?        00:00:00 kswapd0
  729 ?        00:00:00 kseriod
 1100 ?        00:00:00 kjournald
 1125 ?        00:00:00 udevd
 3507 ?        00:00:00 khubd
 3996 ?        00:00:00 shpchpd_event
 5437 ?        00:00:00 dhclient3
 5797 ?        00:00:00 dd
 5799 ?        00:00:00 klogd
 5834 ?        00:00:00 gdm
 5845 ?        00:00:00 gdm
 5882 ?        00:00:14 Xorg
 6536 ?        00:00:00 dbus-daemon-1
 6548 ?        00:00:01 hald
 6561 ?        00:00:00 inetd
 6673 ?        00:00:00 master
 6680 ?        00:00:00 pickup
 6681 ?        00:00:00 qmgr
 6833 ?        00:00:00 anacron
 6844 ?        00:00:00 atd
 6855 ?        00:00:00 cron
 6877 tty1     00:00:00 termwrap
 6878 tty2     00:00:00 getty
 6879 tty3     00:00:00 getty
 6977 tty1     00:00:00 script
 7002 tty1     00:00:00 script
 7003 pts/0    00:00:00 base-config
 7372 pts/0    00:00:00 pkgsel
 7412 ?        00:00:00 x-session-manag
 7463 ?        00:00:00 ssh-agent
 7466 ?        00:00:00 dbus-launch
 7467 ?        00:00:00 dbus-daemon-1
 7481 ?        00:00:00 gconfd-2
 7505 ?        00:00:00 gnome-keyring-d
 7509 ?        00:00:00 esd
 7510 pts/0    00:00:00 aptitude
 7512 ?        00:00:00 bonobo-activati
 7518 ?        00:00:00 gnome-settings-
 7519 pts/0    00:00:00 http
 7520 pts/0    00:00:00 cdrom
 7579 ?        00:00:00 gam_server
 7587 ?        00:00:00 xscreensaver
 7611 ?        00:00:00 gnome-smproxy
 7613 ?        00:00:01 metacity
 7621 ?        00:00:02 gnome-panel
 7623 ?        00:00:03 nautilus
 7625 ?        00:00:00 gnome-volume-ma
 7631 ?        00:00:00 update-notifier
 7634 ?        00:00:00 gnome-cups-icon
 7637 ?        00:00:01 wnck-applet
 7639 ?        00:00:00 trashapplet
 7644 ?        00:00:00 gnome-vfs-daemo
 7651 ?        00:00:00 mapping-daemon
 7656 ?        00:00:00 clock-applet
 7658 ?        00:00:00 mixer_applet2
 7662 ?        00:00:00 notification-ar
 7672 ?        00:00:00 gconfd-2
 7677 ?        00:00:53 firefox-bin
 7704 ?        00:00:01 gaim
 7995 ?        00:00:00 acpid
 8027 ?        00:00:00 cupsd
 8051 ?        00:00:00 gksudo
 8052 ?        00:00:00 synaptic
 8121 ?        00:00:00 syslogd
 8142 ?        00:00:00 gnome-terminal
 8143 ?        00:00:00 gnome-pty-helpe
 8144 pts/1    00:00:00 bash
 8159 pts/1    00:00:00 ps

```

I still have the same problem.. please help !!

---

### Post by Lord Illidan on 2005-08-23
You already have synaptic open, maybe it is in another desktop.  

8052 ?        00:00:00 synaptic

Try putting this in a terminal... ```
killall synaptic
``` 

and reload it with ```
sudo synaptic
```

---

### Post by sml on 2005-09-06
Same problem here also.

What was the solution?

I tried Ctrl-F2 etc and when X is running this does not work.

---

