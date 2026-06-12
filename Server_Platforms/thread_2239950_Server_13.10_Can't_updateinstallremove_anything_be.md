---
title: "Server 13.10: Can't update/install/remove anything because of makedev errors"
date: 2014-08-16
forum: Server Platforms
---

### Post by peacechicken on 2014-08-16
I'm running a web server with 13.10 and can't update, remove, or install any packages. Here's the output of sudo dpkg --configure -a:

```

Setting up makedev (2.3.1-93ubuntu1) ...
mknod: &#8216;mem-&#8217;: Operation not permitted
makedev mem c 1 1 root kmem 0640: failed
mknod: &#8216;kmem-&#8217;: Operation not permitted
makedev kmem c 1 2 root kmem 0640: failed
mknod: &#8216;null-&#8217;: Operation not permitted
makedev null c 1 3 root root 0666: failed
mknod: &#8216;port-&#8217;: Operation not permitted
makedev port c 1 4 root kmem 0640: failed
mknod: &#8216;zero-&#8217;: Operation not permitted
makedev zero c 1 5 root root 0666: failed
mknod: &#8216;full-&#8217;: Operation not permitted
makedev full c 1 7 root root 0666: failed
mknod: &#8216;random-&#8217;: Operation not permitted
makedev random c 1 8 root root 0666: failed
mknod: &#8216;urandom-&#8217;: Operation not permitted
makedev urandom c 1 9 root root 0666: failed
mknod: &#8216;tty-&#8217;: Operation not permitted
makedev tty c 5 0 root tty 0666: failed
mknod: &#8216;ram0-&#8217;: Operation not permitted
makedev ram0 b 1 0 root disk 0660: failed
mknod: &#8216;ram1-&#8217;: Operation not permitted
makedev ram1 b 1 1 root disk 0660: failed
mknod: &#8216;ram2-&#8217;: Operation not permitted
makedev ram2 b 1 2 root disk 0660: failed
mknod: &#8216;ram3-&#8217;: Operation not permitted
makedev ram3 b 1 3 root disk 0660: failed
mknod: &#8216;ram4-&#8217;: Operation not permitted
makedev ram4 b 1 4 root disk 0660: failed
mknod: &#8216;ram5-&#8217;: Operation not permitted
makedev ram5 b 1 5 root disk 0660: failed
mknod: &#8216;ram6-&#8217;: Operation not permitted
makedev ram6 b 1 6 root disk 0660: failed
mknod: &#8216;ram7-&#8217;: Operation not permitted
makedev ram7 b 1 7 root disk 0660: failed
mknod: &#8216;ram8-&#8217;: Operation not permitted
makedev ram8 b 1 8 root disk 0660: failed
mknod: &#8216;ram9-&#8217;: Operation not permitted
makedev ram9 b 1 9 root disk 0660: failed
mknod: &#8216;ram10-&#8217;: Operation not permitted
makedev ram10 b 1 10 root disk 0660: failed
mknod: &#8216;ram11-&#8217;: Operation not permitted
makedev ram11 b 1 11 root disk 0660: failed
mknod: &#8216;ram12-&#8217;: Operation not permitted
makedev ram12 b 1 12 root disk 0660: failed
mknod: &#8216;ram13-&#8217;: Operation not permitted
makedev ram13 b 1 13 root disk 0660: failed
mknod: &#8216;ram14-&#8217;: Operation not permitted
makedev ram14 b 1 14 root disk 0660: failed
mknod: &#8216;ram15-&#8217;: Operation not permitted
makedev ram15 b 1 15 root disk 0660: failed
mknod: &#8216;ram16-&#8217;: Operation not permitted
makedev ram16 b 1 16 root disk 0660: failed
mknod: &#8216;loop0-&#8217;: Operation not permitted
makedev loop0 b 7 0 root disk 0660: failed
mknod: &#8216;loop1-&#8217;: Operation not permitted
makedev loop1 b 7 1 root disk 0660: failed
mknod: &#8216;loop2-&#8217;: Operation not permitted
makedev loop2 b 7 2 root disk 0660: failed
mknod: &#8216;loop3-&#8217;: Operation not permitted
makedev loop3 b 7 3 root disk 0660: failed
mknod: &#8216;loop4-&#8217;: Operation not permitted
makedev loop4 b 7 4 root disk 0660: failed
mknod: &#8216;loop5-&#8217;: Operation not permitted
makedev loop5 b 7 5 root disk 0660: failed
mknod: &#8216;loop6-&#8217;: Operation not permitted
makedev loop6 b 7 6 root disk 0660: failed
mknod: &#8216;loop7-&#8217;: Operation not permitted
makedev loop7 b 7 7 root disk 0660: failed
mknod: &#8216;tty0-&#8217;: Operation not permitted
makedev tty0 c 4 0 root tty 0600: failed
mknod: &#8216;console-&#8217;: Operation not permitted
makedev console c 5 1 root tty 0600: failed
/sbin/MAKEDEV: don't know how to make device "tty0"
dpkg: error processing makedev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on makedev; however:
  Package makedev is not configured yet.

dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on mountall (>= 2.0); however:
  Package mountall is not configured yet.

dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on mountall; however:
  Package mountall is not configured yet.

dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on upstart; however:
  Package upstart is not configured yet.
 initscripts depends on mountall (>= 2.28); however:
  Package mountall is not configured yet.

dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on makedev; however:
  Package makedev is not configured yet.
 ubuntu-minimal depends on upstart; however:
  Package upstart is not configured yet.

dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of rsyslog:
 rsyslog depends on initscripts (>= 2.88dsf-13.3); however:
  Package initscripts is not configured yet.

dpkg: error processing rsyslog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of procps:
 procps depends on initscripts; however:
  Package initscripts is not configured yet.

dpkg: error processing procps (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ifupdown:
 ifupdown depends on initscripts (>= 2.88dsf-25); however:
  Package initscripts is not configured yet.

dpkg: error processing ifupdown (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dbus:
 dbus depends on upstart (>= 0.6.3-6); however:
  Package upstart is not configured yet.

dpkg: error processing dbus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openssh-server:
 openssh-server depends on procps; however:
  Package procps is not configured yet.

dpkg: error processing openssh-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh:
 ssh depends on openssh-server (>= 1:6.2p2-6ubuntu0.3); however:
  Package openssh-server is not configured yet.

dpkg: error processing ssh (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of systemd-services:
 systemd-services depends on dbus; however:
  Package dbus is not configured yet.

dpkg: error processing systemd-services (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd-services (= 204-0ubuntu19.2); however:
  Package systemd-services is not configured yet.

dpkg: error processing libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 makedev
 mountall
 plymouth
 upstart
 initscripts
 ubuntu-minimal
 rsyslog
 procps
 ifupdown
 dbus
 openssh-server
 ssh
 systemd-services
 libpam-systemd:amd64

```

I tried removing it with ```
sudo dpkg --remove makedev
``` and reinstalling with ```
sudo apt-get install makedev
``` but that just spits out the same errors.

---

### Post by Bashing-om on 2014-08-16
peacechicken; Hello;

Release 13.10 is End_Of_Life and no longer has support, the repository has been turned away and no longer exist - as you have known it.

It is advised to upgrade to a current release (12.04, 14.04).

IF the software repository has NOT to this time been turned away - completely- , and you desire to try an online-upgrade
then, - back up all your data  ! - disable all ppa's, revert any proprietary drivers back to open source, disable any screen saver and do:
[terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo do-release-upgrade

```
Else if : [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Else if if : Back up data and do a clean fresh install of the current release.

[INDENT][INDENT]standing still is not an option
[INDENT][INDENT][INDENT]only 3 ways around it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

