---
title: "proftpd not starting with latest kernel"
date: 2010-06-09
forum: Server Platforms
---

### Post by cryptotheslow on 2010-06-09
Hi,

Bit cheeky posting this here I know as I have a desktop install, but the issue is related to proftpd and will probably get more experienced proftpd eyes in the server section than General :)

Running proftpd on Lucid 32bit I have a problem that has me stumped.

On the current kernel 2.6.32-22-generic proftpd does not startup on  system startup - in fact there is no mention of it in any logs,  including the proftpd log files.

From Terminal I try a sudo proftpd and get this:

```

graham@gt-desktop:~$ sudo proftpd
 - notice: unable to bind to Unix domain socket at  '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: Operation not permitted
gt-desktop - 127.0.1.1:21 masquerading as nn.nn.nn.nnn
gt-desktop - mod_delay/0.6: error opening DelayTable  '/var/run/proftpd/proftpd.delay': No such file or directory
gt-desktop - notice: unable to listen to local socket: Operation not  permitted
```If I boot into the previous kernel: 2.6.32-21-generic  proftpd starts up fine on system startup and if I kill it then restart  it I get:

```

graham@gt-desktop:~$ sudo proftpd
 - notice: unable to bind to Unix domain socket at   '/var/run/proftpd/test.sock': No such file or directory
 - notice: unable to listen to local socket: Operation not permitted
gt-desktop - 127.0.1.1:21 masquerading as nn.nn.nn.nnn

```... and it starts up fine.


The weird thing is, is that this did not break right after the kernel  upgrade. It was working fine after that for a couple of days and several  reboots on the new kernel.

The only thing that has changed between it working and not working is  some updates I applied last night as recommended by the Update Manager:

```

Commit Log for Tue Jun  8 20:30:34 2010

Upgraded the following packages:
brasero (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
brasero-common (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
gnome-panel (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
gnome-panel-data (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
libbrasero-media0 (2.30.0-0ubuntu1) to 2.30.1-0ubuntu2
libcairomm-1.0-1 (1.8.0-1build2) to 1.8.4-0ubuntu1
libgcr0 (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libgp11-0 (2.92.92.is.2.30.1-0ubuntu1) to 2.92.92.is.2.30.1-0ubuntu2
libpam-gnome-keyring (2.92.92.is.2.30.1-0ubuntu1) to  2.92.92.is.2.30.1-0ubuntu2
libpanel-applet2-0 (1:2.30.0-0ubuntu1) to 1:2.30.0-0ubuntu2
openoffice.org-base-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-calc (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-common (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-core (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-draw (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-emailmerge (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gnome (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-gtk (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-impress (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-math (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-style-human (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
openoffice.org-writer (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
python-papyon (0.4.6-0ubuntu2) to 0.4.8-0ubuntu1
python-uno (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
rhythmbox (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
rhythmbox-plugin-cdrecorder (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
rhythmbox-plugins (0.12.8-0ubuntu5) to 0.12.8-0ubuntu6
telepathy-butterfly (0.5.8-1ubuntu1) to 0.5.9-0ubuntu1
ttf-opensymbol (1:3.2.0-7ubuntu4) to 1:3.2.0-7ubuntu4.1
tzdata (2010i-1) to 2010j-0ubuntu0.10.04
tzdata-java (2010i-1) to 2010j-0ubuntu0.10.04
uno-libs3 (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1
ure (1.6.0+OOo3.2.0-7ubuntu4) to 1.6.0+OOo3.2.0-7ubuntu4.1

```Since rebooting after that set of updates, proftpd will not start  up - seemingly with some kind of permissions problem... but I can't  work out what. I have reinstalled the proftpd-basic package to no  effect.

Any thoughts on how to fix, or dig deeper into this would be much  appreciated.

Thanks :)

---

### Post by cryptotheslow on 2010-06-11
OK - things get even stranger.

proftpd stopped working on 2.6.32-21-generic as well after a reboot.

I checked and the /var/run/proftpd directory had gone! I manually recreated it and proftpd started up cleanly.

However, following a reboot the /var/run/proftpd directory had gone missing again and proftpd failed to start up.

So actually this seems to be a problem with the /var/run/proftpd directory vanishing. proftpd will run fine on 2.6.32-22-generic as long as that directory is manually created after each reboot.

Any ideas why that directory would vanish on a reboot? Or is it meant to be recreated each time proftpd starts up and for some reason that it is failing to be created and so proftpd fails to start?

---

### Post by cryptotheslow on 2010-06-11
OK some thoughts... /var/run/proftpd contains:
proftpd.delay
proftpd.sock

all the time, even after the proftpd service is stopped.

On starting the proftpd service another file is created:
proftpd.scoreboard

On stopping the service:
proftpd.scoreboard is removed
proftpd.delay is altered in some way (the timestamp on the file changes)

Could it be that during shutdown, the proftpd service stops and tries to write its change to proftpd.delay but the system actually shuts down before the changes are fully committed to disk? i.e. a side-effect of the ext4 journalling??

---

### Post by cryptotheslow on 2010-06-11
After some more digging it looks like /etc/init.d/proftpd actually checks for the existence of /var/run/proftpd and creates it is it doesn't exist.

Near the top it has:

```

# /var/run could be on a tmpfs
[ ! -d /var/run/proftpd ] && mkdir /var/run/proftpd

```

I am absolutely cack at shell scripting but that looked wrong to me so I tried these variants:

```

[ ! test -d /var/run/proftpd ] && mkdir /var/run/proftpd

```

and

```

if ! test -d /var/run/proftpd; then
  mkdir /var/run/proftpd
fi

```

And still the directory is not there following a reboot!

Any ideas welcome!

Thanks :D

---

### Post by cryptotheslow on 2010-06-11
OK... after startup and from a Terminal window, just calling the /etc/init.d/proftpd script creates the missing directory and starts the proftpd daemon fine!

```

graham@gt-desktop:~$ ls -l /var/run
total 44
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 acpid.pid
srw-rw-rw- 1 root       root          0 2010-06-12 00:54 acpid.socket
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 atd.pid
drwxr-xr-x 2 avahi      avahi        80 2010-06-12 00:54 avahi-daemon
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 console
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 ConsoleKit
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 console-kit-daemon.pid
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 crond.pid
---------- 1 root       root          0 2010-06-12 00:54 crond.reboot
drwxr-xr-x 2 messagebus messagebus   80 2010-06-12 00:54 dbus
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 dhclient-eth0.pid
drwx--x--x 4 root       gdm         100 2010-06-12 00:54 gdm
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 gdm.pid
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 network
-rw-r--r-- 1 root       root          3 2010-06-12 00:54 NetworkManager.pid
-rw-r--r-- 1 root       root       1777 2010-06-12 00:54 nm-dhclient-eth0.conf
drwxr-xr-x 4 root       root         80 2010-06-12 00:54 pm-utils
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 rsyslogd.pid
drwxrwxr-x 2 root       utmp         40 2010-06-12 00:54 screen
drwxr-xr-x 2 root       root         40 2010-06-12 00:54 sendsigs.omit.d
drwx------ 3 root       graham       60 2010-06-12 00:56 sudo
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 udev-configure-printer
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 upstart-udev-bridge.pid
-rw-rw-r-- 1 root       utmp       3840 2010-06-12 01:03 utmp

graham@gt-desktop:~$ sudo sh /etc/init.d/proftpd
[sudo] password for graham: 

graham@gt-desktop:~$ sudo sh /etc/init.d/proftpd start
 * Starting ftp server proftpd                                                  gt-desktop - 127.0.1.1:22122 masquerading as 80.46.64.185
                                                                         [ OK ]
graham@gt-desktop:~$ ls -l /var/run
total 48
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 acpid.pid
srw-rw-rw- 1 root       root          0 2010-06-12 00:54 acpid.socket
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 atd.pid
drwxr-xr-x 2 avahi      avahi        80 2010-06-12 00:54 avahi-daemon
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 console
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 ConsoleKit
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 console-kit-daemon.pid
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 crond.pid
---------- 1 root       root          0 2010-06-12 00:54 crond.reboot
drwxr-xr-x 2 messagebus messagebus   80 2010-06-12 00:54 dbus
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 dhclient-eth0.pid
drwx--x--x 4 root       gdm         100 2010-06-12 00:54 gdm
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 gdm.pid
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 network
-rw-r--r-- 1 root       root          3 2010-06-12 00:54 NetworkManager.pid
-rw-r--r-- 1 root       root       1777 2010-06-12 00:54 nm-dhclient-eth0.conf
drwxr-xr-x 4 root       root         80 2010-06-12 00:54 pm-utils
drwxr-xr-x 2 root       root        100 2010-06-12 01:04 proftpd
-rw-r--r-- 1 root       root          5 2010-06-12 01:04 proftpd.pid
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 rsyslogd.pid
drwxrwxr-x 2 root       utmp         40 2010-06-12 00:54 screen
drwxr-xr-x 2 root       root         40 2010-06-12 00:54 sendsigs.omit.d
drwx------ 3 root       graham       60 2010-06-12 00:56 sudo
drwxr-xr-x 2 root       root         60 2010-06-12 00:54 udev-configure-printer
-rw-r--r-- 1 root       root          4 2010-06-12 00:54 upstart-udev-bridge.pid
-rw-rw-r-- 1 root       utmp       3840 2010-06-12 01:03 utmp

```

What on earth is going on here that this does not work during system startup???!

---

