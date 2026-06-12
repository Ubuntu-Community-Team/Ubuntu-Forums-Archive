---
title: "/etc permission problem"
date: 2013-01-02
forum: Server Platforms
---

### Post by SaronaSilverwolf on 2013-01-02
Me and my friend were working on our LAMP server for Ubuntu 12.04, and we accidentally changed the permissions of the /etc directory to 0777 using chmod. Now, we are having a lot of errors and we aren't sure how to change it. Is there a way to change the permissions back to 0440?

---

### Post by lykwydchykyn on 2013-01-02
Did you change it recursively (chmod -R) or just the /etc directory itself?

What happens if you try:
```

sudo chmod 0444 /etc

```

---

### Post by SaronaSilverwolf on 2013-01-02
Just the directory itself. We used: sudo chmod 777 /etc  That is what we used.

Also, trying sudo chmod 0444 /etc gives us this: 

sudo: no valid sudoers sorces found, quiting
sudo: unable to initialize policy plugin

---

### Post by lykwydchykyn on 2013-01-02
> **SaronaSilverwolf said:**
> Just the directory itself. We used: sudo chmod 777 /etc  That is what we used.

Also, trying sudo chmod 0444 /etc gives us this: 

sudo: no valid sudoers sorces found, quiting
sudo: unable to initialize policy plugin

Ok, you can't use sudo because /etc/ is apparently unavailble.  So you'll need to reboot into recovery mode or whatever they're calling it now and get a root console to do this.

This tutorial is a bit dated, but should still work:
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by SaronaSilverwolf on 2013-01-02
Ok, we were able to get into recovery mode, but it's read only. It will not allow us to change the permissions for the /etc directory.

---

### Post by lykwydchykyn on 2013-01-02
> **SaronaSilverwolf said:**
> Ok, we were able to get into recovery mode, but it's read only. It will not allow us to change the permissions for the /etc directory.

Try this then (in recovery mode):
```

mount -o remount,rw /
chmod 0444 /etc

```

---

### Post by steeldriver on 2013-01-02
AFAIK the correct permissions for the /etc *directory *are 755

```
# chmod 755 /etc
```The correct mode for the /etc/sudoers *file *is 440

```
# chmod 440 /etc/sudoers
```Honestly, if you **did **modify permissions recursively on /etc it is probably better to back up your data and reinstall - there are lots of subtle permissions especially on things like sshd files and so on that will take a lot of work to track down and fix

---

### Post by lykwydchykyn on 2013-01-02
> **steeldriver said:**
> Honestly, if you **did **modify permissions recursively on /etc it is probably better to back up your data and reinstall - there are lots of subtle permissions especially on things like sshd files and so on that will take a lot of work to track down and fix

I'll second this, and I kind of suspect that this is what happened, because I don't think you'd get these kinds of errors if only the /etc directory itself had been changed.

If reinstalling is simply out of the question, then you can always recursively chmod 755 and hit the exceptions as they pop up (sudoers, for example).  This could mean a screwy system for weeks or months as permissions problems come to light, though.

---

### Post by fdrake on 2013-01-02
> **SaronaSilverwolf said:**
> Ok, we were able to get into recovery mode, but it's read only. It will not allow us to change the permissions for the /etc directory.

well recovery mode does load some files after all from the system, and if those files are corrupted than fixing it in rec mode makes it hard. I suggest you to boot into a live cd/usb if rec mode does not work. also for permission . 

I also have pasted for you the corrysponding permissions for etc and the contained folders 

```

/etc:
total 1412
drwxr-xr-x 173 root  root     12288 Jan  1 18:47 .
drwxr-xr-x  24 root  root      4096 Nov 23 14:14 ..
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 acpi
-rw-r--r--   1 root  root      2981 Oct 17 10:56 adduser.conf
-rw-r--r--   1 root  root        10 Nov 22 18:06 adjtime
-rw-r--r--   1 root  root       233 Nov 28 01:04 aliases
drwxr-xr-x   2 root  root     12288 Dec 22 08:23 alternatives
-rw-r--r--   1 root  root       401 May 24  2012 anacrontab
-rw-r--r--   1 root  root       112 Oct  1 12:10 apg.conf
drwxr-xr-x   6 root  root      4096 Oct 17 10:58 apm
drwxr-xr-x   3 root  root      4096 Dec 14 18:02 apparmor
drwxr-xr-x   8 root  root      4096 Dec 14 18:10 apparmor.d
drwxr-xr-x   5 root  root      4096 Dec 14 18:10 apport
drwxr-xr-x   6 root  root      4096 Dec 14 17:58 apt
drwxr-xr-x   3 root  root      4096 Oct 17 10:59 aptdaemon
-rw-r-----   1 root  daemon     144 Jun 11  2012 at.deny
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 at-spi2
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 avahi
-rw-r--r--   1 root  root      9085 Nov  6 11:52 avserver.conf
-rw-r--r--   1 root  root      2177 Sep 19 09:42 bash.bashrc
-rw-r--r--   1 root  root        45 Jun 17  2012 bash_completion
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 bash_completion.d
-rw-r--r--   1 root  root       356 Oct  3 21:14 bindresvport.blacklist
-rw-r--r--   1 root  root       321 Sep  6 17:28 blkid.conf
lrwxrwxrwx   1 root  root        15 Nov 22 18:01 blkid.tab -> /dev/.blkid.tab
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 bluetooth
drwxr-xr-x   2 root  root      4096 Nov 27 02:42 bonobo-activation
-rw-r--r--   1 root  root        33 Oct 17 11:00 brlapi.key
drwxr-xr-x   2 root  root     12288 Oct 17 11:00 brltty
-rw-r--r--   1 root  root     21169 Sep 19 11:57 brltty.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 ca-certificates
-rw-r--r--   1 root  root      6854 Oct 17 11:00 ca-certificates.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 calendar
drwxr-s---   2 root  dip       4096 Oct 17 11:00 chatscripts
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 checkbox.d
-rw-r--r--   1 root  root      3682 Apr  7  2012 checkinstallrc
drwxr-xr-x   3 root  root      4096 Nov 28 15:47 cngplp
-rw-r--r--   1 root  root       871 Oct 10 06:30 colord.conf
drwxr-xr-x   3 root  root      4096 Dec 14 18:09 compizconfig
drwxr-xr-x   2 root  root      4096 Nov 22 19:34 conky
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 ConsoleKit
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 console-setup
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cracklib
drwxr-xr-x   2 root  root      4096 Nov 28 01:04 cron.d
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 cron.daily
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 cron.hourly
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cron.monthly
-rw-r--r--   1 root  root       722 Jun 14  2012 crontab
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cron.weekly
-rw-r--r--   1 root  root        67 Nov 22 18:03 crypttab
drwxr-xr-x   4 root  lp        4096 Jan  2 17:19 cups
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cupshelpers
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 dbus-1
drwxr-xr-x   4 root  root      4096 Nov 29 17:16 dconf
-rw-r--r--   1 root  root      2969 Aug 16 13:42 debconf.conf
-rw-r--r--   1 root  root        11 Jul  3  2012 debian_version
drwxr-xr-x   3 root  root      4096 Dec 26 07:39 default
-rw-r--r--   1 root  root       604 May  1  2012 deluser.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 depmod.d
drwxr-xr-x   4 root  root      4096 Dec 14 18:09 dhcp
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 dhcp3
drwxr-xr-x   2 root  root      4096 Nov 22 18:08 dictionaries-common
drwxr-xr-x   3 root  root      4096 Nov 28 20:47 dkms
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 dnsmasq.d
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 doc-base
drwxr-xr-x   4 root  root      4096 Nov 26 18:36 dpkg
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 emacs
-rw-r--r--   1 root  root        96 Oct 17 10:56 environment
drwxr-xr-x   2 root  root      4096 Nov 22 18:56 esound
drwxr-xr-x   3 root  root      4096 Dec 14 18:10 firefox
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 fonts
drwxr-xr-x   3 root  root      4096 Oct 17 10:59 foomatic
-rw-r--r--   1 root  root       635 Nov 22 18:03 fstab
drwxr-xr-x   2 root  root      4096 Sep  6 17:28 fstab.d
-rw-r-----   1 root  fuse       216 Oct 18  2011 fuse.conf
-rw-r--r--   1 root  root      3343 Oct  3 21:14 gai.conf
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 gconf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 gdb
drwxr-xr-x   6 root  root      4096 Nov 29 17:22 gdm
drwxr-xr-x   4 root  root      4096 Oct 17 10:58 ghostscript
drwxr-xr-x   3 root  root      4096 Nov 27 05:06 gimp
-rw-r--r--   1 root  root       580 Jul 16 00:05 gnashpluginrc
-rw-r--r--   1 root  root      5597 Jul 16 00:05 gnashrc
-rw-r--r--   1 root  root       690 Jul 16 00:05 gnashthumbnailrc
drwxr-xr-x   3 root  root      4096 Nov 29 17:17 gnome
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 gnome-app-install
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 gnome-settings-daemon
drwxr-xr-x   3 root  root      4096 Nov 27 02:42 gnome-vfs-2.0
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 groff
-rw-r--r--   1 root  root       998 Nov 29 17:23 group
-rw-------   1 root  root       978 Nov 29 17:22 group-
drwxr-xr-x   2 root  root      4096 Dec  7 07:45 grub.d
-rw-r-----   1 root  shadow     826 Nov 29 17:23 gshadow
-rw-------   1 root  root       809 Nov 29 17:22 gshadow-
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 gtk-2.0
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 gtk-3.0
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 gtkmathview
-rw-r--r--   1 root  root      4728 May  1  2012 hdparm.conf
-rw-r--r--   1 root  root        92 Jul  3  2012 host.conf
-rw-r--r--   1 root  root         4 Nov 22 18:06 hostname
-rw-r--r--   1 root  root       218 Nov 22 18:06 hosts
-rw-r--r--   1 root  root       594 Nov 28 01:04 hosts.allow
-rw-r--r--   1 root  root       880 Oct 17 10:59 hosts.deny
drwxr-xr-x   3 root  root      4096 Nov 29 17:17 hotplug
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 hp
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 ifplugd
drwxr-xr-x   2 root  root      4096 Nov 26 01:09 ImageMagick
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 init
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 init.d
drwxr-xr-x   3 root  root      4096 Dec 23 21:30 initramfs
drwxr-xr-x   5 root  root      4096 Oct 17 10:56 initramfs-tools
-rw-r--r--   1 root  root      1721 Sep 18 08:21 inputrc
drwxr-xr-x   3 root  root      4096 Aug 10 10:49 insserv
-rw-r--r--   1 root  root       839 Aug 10 10:49 insserv.conf
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 insserv.conf.d
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 iproute2
-rw-r--r--   1 root  root        20 Oct  9 10:59 issue
-rw-r--r--   1 root  root        13 Oct  9 10:59 issue.net
drwxr-xr-x   3 root  root      4096 Dec  4 14:02 .java
drwxr-xr-x   2 root  root      4096 Dec  4 14:02 java-6-openjdk
drwxr-xr-x   5 root  root      4096 Dec  4 14:02 java-7-openjdk
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 kbd
drwxr-xr-x   6 root  root      4096 Nov 28 20:46 kernel
-rw-r--r--   1 root  root       110 Nov 22 18:09 kernel-img.conf
-rw-r--r--   1 root  root      1311 Jul 20 12:58 kerneloops.conf
lrwxrwxrwx   1 root  root         4 Sep 24 15:58 kvm -> qemu
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 ldap
-rw-r--r--   1 root  root    117489 Jan  1 18:47 ld.so.cache
-rw-r--r--   1 root  root        34 Oct 17 10:56 ld.so.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 ld.so.conf.d
-rw-r--r--   1 root  root       267 Jul  3  2012 legal
-rw-r--r--   1 root  root       191 Jan 15  2012 libaudit.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 libnl-3
drwxr-xr-x   2 root  root      4096 May 30  2012 libpaper.d
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 libreoffice
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 lightdm
-rw-r--r--   1 root  root      1291 Sep 28 12:38 lintianrc
-rw-r--r--   1 root  root      2570 Aug  5  2010 locale.alias
-rw-r--r--   1 root  root      3519 Nov 22 18:06 localtime
drwxr-xr-x   6 root  root      4096 Nov 28 01:04 logcheck
-rw-r--r--   1 root  root     10551 Sep  6 15:14 login.defs
-rw-r--r--   1 root  root       599 Oct  4  2011 logrotate.conf
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 logrotate.d
drwxr-xr-x   2 root  root      4096 Oct 10 14:31 lsb-base
-rw-r--r--   1 root  root      3279 Aug 14 22:17 lsb-base-logging.sh
-rw-r--r--   1 root  root       100 Oct  9 08:14 lsb-release
-rw-r--r--   1 root  root     15752 Jul 25  2009 ltrace.conf
-rw-r--r--   1 root  root       111 Jun 30  2012 magic
-rw-r--r--   1 root  root       111 Jun 30  2012 magic.mime
drwxr-sr-x   7 smmta smmsp     4096 Nov 29 17:21 mail
-rw-r--r--   1 root  root     29362 Dec 21 04:10 mailcap
-rw-r--r--   1 root  root       449 Jul 16 05:12 mailcap.order
-rw-r--r--   1 root  root      5173 Sep 18 18:44 manpath.config
drwxr-xr-x   2 root  root      4096 Nov 26 19:20 mc
drwxr-xr-x   2 root  root      4096 Nov 29 17:20 menu
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 menu-methods
drwxr-xr-x   3 root  root      4096 Nov 26 19:17 mercurial
-rw-r--r--   1 root  root     24269 Jul 16 05:12 mime.types
-rw-r--r--   1 root  root       956 Aug 22 18:33 mke2fs.conf
drwxr-xr-x   2 root  root      4096 Nov 28 20:47 modprobe.d
-rw-r--r--   1 root  root       203 Nov 22 18:08 modules
drwxr-xr-x   4 root  root      4096 Nov 29 17:23 mono
lrwxrwxrwx   1 root  root        13 Nov 22 18:01 motd -> /var/run/motd
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich2
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich-mpd
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich-shmem
drwxr-xr-x   2 root  root      4096 Nov 22 18:57 mplayer
-rw-r--r--   1 root  root       936 Jan  1 18:26 mtab
-rw-------   1 root  lightdm      0 Nov 22 18:26 mtab.fuselock
-rw-r--r--   1 root  root       624 Aug  8  2007 mtools.conf
-rw-r--r--   1 root  root      8453 Oct  1 10:11 nanorc
-rw-r--r--   1 root  root      2064 Nov 23  2006 netscsid.conf
drwxr-xr-x   6 root  root      4096 Oct 17 10:56 network
drwxr-xr-x   6 root  root      4096 Oct 17 11:00 NetworkManager
-rw-r--r--   1 root  root        91 Jul  3  2012 networks
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 newt
-rw-r--r--   1 root  root       513 Oct 17 11:00 nsswitch.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 obex-data-server
-rw-r--r--   1 root  root       109 Jun  8  2012 ocamlfind.conf
-rw-r--r--   1 root  root      1172 Sep  6 04:37 octave.conf
drwxr-xr-x   2 root  root      4096 Oct  8 19:26 ODBCDataSources
-rw-r--r--   1 root  root         0 Oct  8 19:26 odbc.ini
-rw-r--r--   1 root  root         0 Nov 26 01:09 odbcinst.ini
drwxr-xr-x   2 root  root      4096 Nov 22 18:12 openal
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 openvpn
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 opt
-rw-r--r--   1 root  root       128 Oct 23 17:53 os-release
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 PackageKit
-rw-r--r--   1 root  root       552 Jul  3  2012 pam.conf
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 pam.d
-rw-r--r--   1 root  root         7 Nov 22 18:08 papersize
-rw-r--r--   1 root  root      1911 Nov 29 17:23 passwd
-rw-------   1 root  root      1911 Nov 29 17:23 passwd-
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 pcmcia
drwxr-xr-x   4 root  root      4096 Oct 17 10:58 perl
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 pkcs11
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 pm
-rw-r--r--   1 root  root      7649 Oct 17 11:00 pnm2ppa.conf
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 polkit-1
-rw-r--r--   1 root  root       350 Nov 22 18:08 popularity-contest.conf
drwxr-xr-x   8 root  root      4096 Oct 17 11:00 ppp
lrwxrwxrwx   1 root  root        22 Dec 14 18:08 printcap -> /var/run/cups/printcap
-rw-r--r--   1 root  root       665 Dec 14 17:58 profile
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 profile.d
-rw-r--r--   1 root  root      2933 Jul  3  2012 protocols
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 pulse
-rw-------   1 root  root         0 Oct 17 10:56 .pwd.lock
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 python
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 python2.7
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 python3
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 python3.2
drwxr-xr-x   2 root  root      4096 Nov 28 02:34 qemu
lrwxrwxrwx   1 root  root        20 Sep 24 15:58 qemu-ifdown -> /usr/bin/qemu-ifdown
lrwxrwxrwx   1 root  root        18 Sep 24 15:58 qemu-ifup -> /usr/bin/qemu-ifup
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc0.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc1.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc2.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc3.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc4.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc5.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc6.d
-rwxr-xr-x   1 root  root       306 Oct 17 10:56 rc.local
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 rcS.d
-rw-r--r--   1 root  root       121 Oct  4 05:41 remote-login-service.conf
-rw-r--r--   1 root  root      1889 Jun 30  2012 request-key.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:01 request-key.d
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 resolvconf
lrwxrwxrwx   1 root  root        29 Nov 22 18:06 resolv.conf -> ../run/resolvconf/resolv.conf
-rwxr-xr-x   1 root  root       268 Mar 30  2012 rmt
-rw-r--r--   1 root  root       887 Jul  3  2012 rpc
-rw-r--r--   1 root  root      1263 Mar 30  2012 rsyslog.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 rsyslog.d
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 samba
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 sane.d
-rw-r--r--   1 root  root      3902 Sep  6 15:14 securetty
drwxr-xr-x   4 root  root      4096 Oct 17 11:00 security
-rw-r--r--   1 root  root     10333 Oct  5 07:36 sensors3.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 sensors.d
-rw-r--r--   1 root  root     19398 Jul  3  2012 services
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 sgml
-rw-r-----   1 root  shadow    1155 Nov 29 17:23 shadow
-rw-------   1 root  root      1155 Nov 29 17:23 shadow-
-rw-r--r--   1 root  root        84 Nov 22 18:58 shells
-rw-r--r--   1 root  root       657 Sep 19 15:08 signond.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 signon-ui
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 skel
-rw-r--r--   1 root  root      1132 Jun  8  2012 smi.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 snmp
drwxr-xr-x   3 root  root      4096 Nov 27 02:42 sound
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 spamassassin
drwxr-xr-x   4 root  root      4096 Oct 17 11:00 speech-dispatcher
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 ssh
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 ssl
drwxr-xr-x   2 root  root      4096 Nov 26 19:17 subversion
-r--r-----   1 root  root       745 Jul 16 08:13 sudoers
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 sudoers.d
-rw-r--r--   1 root  root        19 May  1  2011 su-to-rootrc
-rw-r--r--   1 root  root      2083 Nov 15  2011 sysctl.conf
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 sysctl.d
drwxr-xr-x   3 root  root      4096 Oct 17 10:56 systemd
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 terminfo
drwxr-xr-x   3 root  root      4096 Nov 27 02:56 texmf
drwxr-xr-x   2 root  root      4096 Nov 22 18:08 thunderbird
-rw-r--r--   1 root  root        17 Nov 22 18:06 timezone
drwxr-xr-x   2 root  root      4096 Nov 22 18:13 timidity
-rw-r--r--   1 root  root       645 May  1  2012 ts.conf
-rw-r--r--   1 root  root      1260 May 30  2008 ucf.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:56 udev
drwxr-xr-x   2 root  root      4096 Oct  9 15:45 udisks2
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 ufw
-rw-r--r--   1 root  root       326 Aug 14 23:26 updatedb.conf
drwxr-xr-x   3 root  root      4096 Dec 14 18:10 update-manager
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 update-motd.d
drwxr-xr-x   2 root  root      4096 Oct  9 18:41 update-notifier
-rw-r--r--   1 root  root        32 Oct  9  2011 upek.cfg
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 UPower
-rw-r--r--   1 root  root       572 Oct  8 22:08 usb_modeswitch.conf
drwxr-xr-x   2 root  root      4096 Sep 19 09:13 usb_modeswitch.d
-rw-r--r--   1 root  root        51 Jun 15  2012 vdpau_wrapper.cfg
drwxr-xr-x   2 root  root      4096 Nov 22 18:57 vga
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 vim
drwxr-xr-x   3 root  root      4096 Nov 22 18:56 vlc
lrwxrwxrwx   1 root  root        23 Nov 22 18:01 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r--   1 root  root      4496 Jun 14  2012 wgetrc
drwxr-xr-x   2 root  root      4096 Nov 22 18:12 wildmidi
drwxr-xr-x   2 root  root      4096 Dec 22 08:48 wireshark
-rw-r--r--   1 root  root      1343 Jan  9  2007 wodim.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 wpa_supplicant
drwxr-xr-x  10 root  root      4096 Nov 29 17:22 X11
drwxr-xr-x   5 root  root      4096 Oct 17 11:00 xdg
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 xml
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 xul-ext
-rw-r--r--   1 root  root       349 Jan 13  2012 zsh_command_not_found
/etc:
total 1412
drwxr-xr-x 173 root  root     12288 Jan  1 18:47 .
drwxr-xr-x  24 root  root      4096 Nov 23 14:14 ..
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 acpi
-rw-r--r--   1 root  root      2981 Oct 17 10:56 adduser.conf
-rw-r--r--   1 root  root        10 Nov 22 18:06 adjtime
-rw-r--r--   1 root  root       233 Nov 28 01:04 aliases
drwxr-xr-x   2 root  root     12288 Dec 22 08:23 alternatives
-rw-r--r--   1 root  root       401 May 24  2012 anacrontab
-rw-r--r--   1 root  root       112 Oct  1 12:10 apg.conf
drwxr-xr-x   6 root  root      4096 Oct 17 10:58 apm
drwxr-xr-x   3 root  root      4096 Dec 14 18:02 apparmor
drwxr-xr-x   8 root  root      4096 Dec 14 18:10 apparmor.d
drwxr-xr-x   5 root  root      4096 Dec 14 18:10 apport
drwxr-xr-x   6 root  root      4096 Dec 14 17:58 apt
drwxr-xr-x   3 root  root      4096 Oct 17 10:59 aptdaemon
-rw-r-----   1 root  daemon     144 Jun 11  2012 at.deny
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 at-spi2
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 avahi
-rw-r--r--   1 root  root      9085 Nov  6 11:52 avserver.conf
-rw-r--r--   1 root  root      2177 Sep 19 09:42 bash.bashrc
-rw-r--r--   1 root  root        45 Jun 17  2012 bash_completion
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 bash_completion.d
-rw-r--r--   1 root  root       356 Oct  3 21:14 bindresvport.blacklist
-rw-r--r--   1 root  root       321 Sep  6 17:28 blkid.conf
lrwxrwxrwx   1 root  root        15 Nov 22 18:01 blkid.tab -> /dev/.blkid.tab
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 bluetooth
drwxr-xr-x   2 root  root      4096 Nov 27 02:42 bonobo-activation
-rw-r--r--   1 root  root        33 Oct 17 11:00 brlapi.key
drwxr-xr-x   2 root  root     12288 Oct 17 11:00 brltty
-rw-r--r--   1 root  root     21169 Sep 19 11:57 brltty.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 ca-certificates
-rw-r--r--   1 root  root      6854 Oct 17 11:00 ca-certificates.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 calendar
drwxr-s---   2 root  dip       4096 Oct 17 11:00 chatscripts
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 checkbox.d
-rw-r--r--   1 root  root      3682 Apr  7  2012 checkinstallrc
drwxr-xr-x   3 root  root      4096 Nov 28 15:47 cngplp
-rw-r--r--   1 root  root       871 Oct 10 06:30 colord.conf
drwxr-xr-x   3 root  root      4096 Dec 14 18:09 compizconfig
drwxr-xr-x   2 root  root      4096 Nov 22 19:34 conky
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 ConsoleKit
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 console-setup
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cracklib
drwxr-xr-x   2 root  root      4096 Nov 28 01:04 cron.d
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 cron.daily
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 cron.hourly
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cron.monthly
-rw-r--r--   1 root  root       722 Jun 14  2012 crontab
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cron.weekly
-rw-r--r--   1 root  root        67 Nov 22 18:03 crypttab
drwxr-xr-x   4 root  lp        4096 Jan  2 17:19 cups
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cupshelpers
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 dbus-1
drwxr-xr-x   4 root  root      4096 Nov 29 17:16 dconf
-rw-r--r--   1 root  root      2969 Aug 16 13:42 debconf.conf
-rw-r--r--   1 root  root        11 Jul  3  2012 debian_version
drwxr-xr-x   3 root  root      4096 Dec 26 07:39 default
-rw-r--r--   1 root  root       604 May  1  2012 deluser.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 depmod.d
drwxr-xr-x   4 root  root      4096 Dec 14 18:09 dhcp
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 dhcp3
drwxr-xr-x   2 root  root      4096 Nov 22 18:08 dictionaries-common
drwxr-xr-x   3 root  root      4096 Nov 28 20:47 dkms
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 dnsmasq.d
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 doc-base
drwxr-xr-x   4 root  root      4096 Nov 26 18:36 dpkg
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 emacs
-rw-r--r--   1 root  root        96 Oct 17 10:56 environment
drwxr-xr-x   2 root  root      4096 Nov 22 18:56 esound
drwxr-xr-x   3 root  root      4096 Dec 14 18:10 firefox
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 fonts
drwxr-xr-x   3 root  root      4096 Oct 17 10:59 foomatic
-rw-r--r--   1 root  root       635 Nov 22 18:03 fstab
drwxr-xr-x   2 root  root      4096 Sep  6 17:28 fstab.d
-rw-r-----   1 root  fuse       216 Oct 18  2011 fuse.conf
-rw-r--r--   1 root  root      3343 Oct  3 21:14 gai.conf
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 gconf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 gdb
drwxr-xr-x   6 root  root      4096 Nov 29 17:22 gdm
drwxr-xr-x   4 root  root      4096 Oct 17 10:58 ghostscript
drwxr-xr-x   3 root  root      4096 Nov 27 05:06 gimp
-rw-r--r--   1 root  root       580 Jul 16 00:05 gnashpluginrc
-rw-r--r--   1 root  root      5597 Jul 16 00:05 gnashrc
-rw-r--r--   1 root  root       690 Jul 16 00:05 gnashthumbnailrc
drwxr-xr-x   3 root  root      4096 Nov 29 17:17 gnome
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 gnome-app-install
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 gnome-settings-daemon
drwxr-xr-x   3 root  root      4096 Nov 27 02:42 gnome-vfs-2.0
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 groff
-rw-r--r--   1 root  root       998 Nov 29 17:23 group
-rw-------   1 root  root       978 Nov 29 17:22 group-
drwxr-xr-x   2 root  root      4096 Dec  7 07:45 grub.d
-rw-r-----   1 root  shadow     826 Nov 29 17:23 gshadow
-rw-------   1 root  root       809 Nov 29 17:22 gshadow-
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 gtk-2.0
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 gtk-3.0
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 gtkmathview
-rw-r--r--   1 root  root      4728 May  1  2012 hdparm.conf
-rw-r--r--   1 root  root        92 Jul  3  2012 host.conf
-rw-r--r--   1 root  root         4 Nov 22 18:06 hostname
-rw-r--r--   1 root  root       218 Nov 22 18:06 hosts
-rw-r--r--   1 root  root       594 Nov 28 01:04 hosts.allow
-rw-r--r--   1 root  root       880 Oct 17 10:59 hosts.deny
drwxr-xr-x   3 root  root      4096 Nov 29 17:17 hotplug
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 hp
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 ifplugd
drwxr-xr-x   2 root  root      4096 Nov 26 01:09 ImageMagick
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 init
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 init.d
drwxr-xr-x   3 root  root      4096 Dec 23 21:30 initramfs
drwxr-xr-x   5 root  root      4096 Oct 17 10:56 initramfs-tools
-rw-r--r--   1 root  root      1721 Sep 18 08:21 inputrc
drwxr-xr-x   3 root  root      4096 Aug 10 10:49 insserv
-rw-r--r--   1 root  root       839 Aug 10 10:49 insserv.conf
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 insserv.conf.d
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 iproute2
-rw-r--r--   1 root  root        20 Oct  9 10:59 issue
-rw-r--r--   1 root  root        13 Oct  9 10:59 issue.net
drwxr-xr-x   3 root  root      4096 Dec  4 14:02 .java
drwxr-xr-x   2 root  root      4096 Dec  4 14:02 java-6-openjdk
drwxr-xr-x   5 root  root      4096 Dec  4 14:02 java-7-openjdk
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 kbd
drwxr-xr-x   6 root  root      4096 Nov 28 20:46 kernel
-rw-r--r--   1 root  root       110 Nov 22 18:09 kernel-img.conf
-rw-r--r--   1 root  root      1311 Jul 20 12:58 kerneloops.conf
lrwxrwxrwx   1 root  root         4 Sep 24 15:58 kvm -> qemu
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 ldap
-rw-r--r--   1 root  root    117489 Jan  1 18:47 ld.so.cache
-rw-r--r--   1 root  root        34 Oct 17 10:56 ld.so.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 ld.so.conf.d
-rw-r--r--   1 root  root       267 Jul  3  2012 legal
-rw-r--r--   1 root  root       191 Jan 15  2012 libaudit.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 libnl-3
drwxr-xr-x   2 root  root      4096 May 30  2012 libpaper.d
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 libreoffice
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 lightdm
-rw-r--r--   1 root  root      1291 Sep 28 12:38 lintianrc
-rw-r--r--   1 root  root      2570 Aug  5  2010 locale.alias
-rw-r--r--   1 root  root      3519 Nov 22 18:06 localtime
drwxr-xr-x   6 root  root      4096 Nov 28 01:04 logcheck
-rw-r--r--   1 root  root     10551 Sep  6 15:14 login.defs
-rw-r--r--   1 root  root       599 Oct  4  2011 logrotate.conf
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 logrotate.d
drwxr-xr-x   2 root  root      4096 Oct 10 14:31 lsb-base
-rw-r--r--   1 root  root      3279 Aug 14 22:17 lsb-base-logging.sh
-rw-r--r--   1 root  root       100 Oct  9 08:14 lsb-release
-rw-r--r--   1 root  root     15752 Jul 25  2009 ltrace.conf
-rw-r--r--   1 root  root       111 Jun 30  2012 magic
-rw-r--r--   1 root  root       111 Jun 30  2012 magic.mime
drwxr-sr-x   7 smmta smmsp     4096 Nov 29 17:21 mail
-rw-r--r--   1 root  root     29362 Dec 21 04:10 mailcap
-rw-r--r--   1 root  root       449 Jul 16 05:12 mailcap.order
-rw-r--r--   1 root  root      5173 Sep 18 18:44 manpath.config
drwxr-xr-x   2 root  root      4096 Nov 26 19:20 mc
drwxr-xr-x   2 root  root      4096 Nov 29 17:20 menu
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 menu-methods
drwxr-xr-x   3 root  root      4096 Nov 26 19:17 mercurial
-rw-r--r--   1 root  root     24269 Jul 16 05:12 mime.types
-rw-r--r--   1 root  root       956 Aug 22 18:33 mke2fs.conf
drwxr-xr-x   2 root  root      4096 Nov 28 20:47 modprobe.d
-rw-r--r--   1 root  root       203 Nov 22 18:08 modules
drwxr-xr-x   4 root  root      4096 Nov 29 17:23 mono
lrwxrwxrwx   1 root  root        13 Nov 22 18:01 motd -> /var/run/motd
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich2
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich-mpd
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich-shmem
drwxr-xr-x   2 root  root      4096 Nov 22 18:57 mplayer
-rw-r--r--   1 root  root       936 Jan  1 18:26 mtab
-rw-------   1 root  lightdm      0 Nov 22 18:26 mtab.fuselock
-rw-r--r--   1 root  root       624 Aug  8  2007 mtools.conf
-rw-r--r--   1 root  root      8453 Oct  1 10:11 nanorc
-rw-r--r--   1 root  root      2064 Nov 23  2006 netscsid.conf
drwxr-xr-x   6 root  root      4096 Oct 17 10:56 network
drwxr-xr-x   6 root  root      4096 Oct 17 11:00 NetworkManager
-rw-r--r--   1 root  root        91 Jul  3  2012 networks
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 newt
-rw-r--r--   1 root  root       513 Oct 17 11:00 nsswitch.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 obex-data-server
-rw-r--r--   1 root  root       109 Jun  8  2012 ocamlfind.conf
-rw-r--r--   1 root  root      1172 Sep  6 04:37 octave.conf
drwxr-xr-x   2 root  root      4096 Oct  8 19:26 ODBCDataSources
-rw-r--r--   1 root  root         0 Oct  8 19:26 odbc.ini
-rw-r--r--   1 root  root         0 Nov 26 01:09 odbcinst.ini
drwxr-xr-x   2 root  root      4096 Nov 22 18:12 openal
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 openvpn
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 opt
-rw-r--r--   1 root  root       128 Oct 23 17:53 os-release
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 PackageKit
-rw-r--r--   1 root  root       552 Jul  3  2012 pam.conf
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 pam.d
-rw-r--r--   1 root  root         7 Nov 22 18:08 papersize
-rw-r--r--   1 root  root      1911 Nov 29 17:23 passwd
-rw-------   1 root  root      1911 Nov 29 17:23 passwd-
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 pcmcia
drwxr-xr-x   4 root  root      4096 Oct 17 10:58 perl
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 pkcs11
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 pm
-rw-r--r--   1 root  root      7649 Oct 17 11:00 pnm2ppa.conf
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 polkit-1
-rw-r--r--   1 root  root       350 Nov 22 18:08 popularity-contest.conf
drwxr-xr-x   8 root  root      4096 Oct 17 11:00 ppp
lrwxrwxrwx   1 root  root        22 Dec 14 18:08 printcap -> /var/run/cups/printcap
-rw-r--r--   1 root  root       665 Dec 14 17:58 profile
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 profile.d
-rw-r--r--   1 root  root      2933 Jul  3  2012 protocols
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 pulse
-rw-------   1 root  root         0 Oct 17 10:56 .pwd.lock
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 python
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 python2.7
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 python3
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 python3.2
drwxr-xr-x   2 root  root      4096 Nov 28 02:34 qemu
lrwxrwxrwx   1 root  root        20 Sep 24 15:58 qemu-ifdown -> /usr/bin/qemu-ifdown
lrwxrwxrwx   1 root  root        18 Sep 24 15:58 qemu-ifup -> /usr/bin/qemu-ifup
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc0.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc1.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc2.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc3.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc4.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc5.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc6.d
-rwxr-xr-x   1 root  root       306 Oct 17 10:56 rc.local
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 rcS.d
-rw-r--r--   1 root  root       121 Oct  4 05:41 remote-login-service.conf
-rw-r--r--   1 root  root      1889 Jun 30  2012 request-key.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:01 request-key.d
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 resolvconf
lrwxrwxrwx   1 root  root        29 Nov 22 18:06 resolv.conf -> ../run/resolvconf/resolv.conf
-rwxr-xr-x   1 root  root       268 Mar 30  2012 rmt
-rw-r--r--   1 root  root       887 Jul  3  2012 rpc
-rw-r--r--   1 root  root      1263 Mar 30  2012 rsyslog.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 rsyslog.d
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 samba
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 sane.d
-rw-r--r--   1 root  root      3902 Sep  6 15:14 securetty
drwxr-xr-x   4 root  root      4096 Oct 17 11:00 security
-rw-r--r--   1 root  root     10333 Oct  5 07:36 sensors3.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 sensors.d
-rw-r--r--   1 root  root     19398 Jul  3  2012 services
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 sgml
-rw-r-----   1 root  shadow    1155 Nov 29 17:23 shadow
-rw-------   1 root  root      1155 Nov 29 17:23 shadow-
-rw-r--r--   1 root  root        84 Nov 22 18:58 shells
-rw-r--r--   1 root  root       657 Sep 19 15:08 signond.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 signon-ui
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 skel
-rw-r--r--   1 root  root      1132 Jun  8  2012 smi.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 snmp
drwxr-xr-x   3 root  root      4096 Nov 27 02:42 sound
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 spamassassin
drwxr-xr-x   4 root  root      4096 Oct 17 11:00 speech-dispatcher
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 ssh
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 ssl
drwxr-xr-x   2 root  root      4096 Nov 26 19:17 subversion
-r--r-----   1 root  root       745 Jul 16 08:13 sudoers
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 sudoers.d
-rw-r--r--   1 root  root        19 May  1  2011 su-to-rootrc
-rw-r--r--   1 root  root      2083 Nov 15  2011 sysctl.conf
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 sysctl.d
drwxr-xr-x   3 root  root      4096 Oct 17 10:56 systemd
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 terminfo
drwxr-xr-x   3 root  root      4096 Nov 27 02:56 texmf
drwxr-xr-x   2 root  root      4096 Nov 22 18:08 thunderbird
-rw-r--r--   1 root  root        17 Nov 22 18:06 timezone
drwxr-xr-x   2 root  root      4096 Nov 22 18:13 timidity
-rw-r--r--   1 root  root       645 May  1  2012 ts.conf
-rw-r--r--   1 root  root      1260 May 30  2008 ucf.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:56 udev
drwxr-xr-x   2 root  root      4096 Oct  9 15:45 udisks2
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 ufw
-rw-r--r--   1 root  root       326 Aug 14 23:26 updatedb.conf
drwxr-xr-x   3 root  root      4096 Dec 14 18:10 update-manager
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 update-motd.d
drwxr-xr-x   2 root  root      4096 Oct  9 18:41 update-notifier
-rw-r--r--   1 root  root        32 Oct  9  2011 upek.cfg
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 UPower
-rw-r--r--   1 root  root       572 Oct  8 22:08 usb_modeswitch.conf
drwxr-xr-x   2 root  root      4096 Sep 19 09:13 usb_modeswitch.d
-rw-r--r--   1 root  root        51 Jun 15  2012 vdpau_wrapper.cfg
drwxr-xr-x   2 root  root      4096 Nov 22 18:57 vga
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 vim
drwxr-xr-x   3 root  root      4096 Nov 22 18:56 vlc
lrwxrwxrwx   1 root  root        23 Nov 22 18:01 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r--   1 root  root      4496 Jun 14  2012 wgetrc
drwxr-xr-x   2 root  root      4096 Nov 22 18:12 wildmidi
drwxr-xr-x   2 root  root      4096 Dec 22 08:48 wireshark
-rw-r--r--   1 root  root      1343 Jan  9  2007 wodim.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 wpa_supplicant
drwxr-xr-x  10 root  root      4096 Nov 29 17:22 X11
drwxr-xr-x   5 root  root      4096 Oct 17 11:00 xdg
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 xml
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 xul-ext
-rw-r--r--   1 root  root       349 Jan 13  2012 zsh_command_not_found
total 1412
drwxr-xr-x 173 root  root     12288 Jan  1 18:47 .
drwxr-xr-x  24 root  root      4096 Nov 23 14:14 ..
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 acpi
-rw-r--r--   1 root  root      2981 Oct 17 10:56 adduser.conf
-rw-r--r--   1 root  root        10 Nov 22 18:06 adjtime
-rw-r--r--   1 root  root       233 Nov 28 01:04 aliases
drwxr-xr-x   2 root  root     12288 Dec 22 08:23 alternatives
-rw-r--r--   1 root  root       401 May 24  2012 anacrontab
-rw-r--r--   1 root  root       112 Oct  1 12:10 apg.conf
drwxr-xr-x   6 root  root      4096 Oct 17 10:58 apm
drwxr-xr-x   3 root  root      4096 Dec 14 18:02 apparmor
drwxr-xr-x   8 root  root      4096 Dec 14 18:10 apparmor.d
drwxr-xr-x   5 root  root      4096 Dec 14 18:10 apport
drwxr-xr-x   6 root  root      4096 Dec 14 17:58 apt
drwxr-xr-x   3 root  root      4096 Oct 17 10:59 aptdaemon
-rw-r-----   1 root  daemon     144 Jun 11  2012 at.deny
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 at-spi2
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 avahi
-rw-r--r--   1 root  root      9085 Nov  6 11:52 avserver.conf
-rw-r--r--   1 root  root      2177 Sep 19 09:42 bash.bashrc
-rw-r--r--   1 root  root        45 Jun 17  2012 bash_completion
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 bash_completion.d
-rw-r--r--   1 root  root       356 Oct  3 21:14 bindresvport.blacklist
-rw-r--r--   1 root  root       321 Sep  6 17:28 blkid.conf
lrwxrwxrwx   1 root  root        15 Nov 22 18:01 blkid.tab -> /dev/.blkid.tab
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 bluetooth
drwxr-xr-x   2 root  root      4096 Nov 27 02:42 bonobo-activation
-rw-r--r--   1 root  root        33 Oct 17 11:00 brlapi.key
drwxr-xr-x   2 root  root     12288 Oct 17 11:00 brltty
-rw-r--r--   1 root  root     21169 Sep 19 11:57 brltty.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 ca-certificates
-rw-r--r--   1 root  root      6854 Oct 17 11:00 ca-certificates.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 calendar
drwxr-s---   2 root  dip       4096 Oct 17 11:00 chatscripts
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 checkbox.d
-rw-r--r--   1 root  root      3682 Apr  7  2012 checkinstallrc
drwxr-xr-x   3 root  root      4096 Nov 28 15:47 cngplp
-rw-r--r--   1 root  root       871 Oct 10 06:30 colord.conf
drwxr-xr-x   3 root  root      4096 Dec 14 18:09 compizconfig
drwxr-xr-x   2 root  root      4096 Nov 22 19:34 conky
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 ConsoleKit
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 console-setup
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cracklib
drwxr-xr-x   2 root  root      4096 Nov 28 01:04 cron.d
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 cron.daily
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 cron.hourly
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cron.monthly
-rw-r--r--   1 root  root       722 Jun 14  2012 crontab
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cron.weekly
-rw-r--r--   1 root  root        67 Nov 22 18:03 crypttab
drwxr-xr-x   4 root  lp        4096 Jan  2 17:19 cups
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 cupshelpers
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 dbus-1
drwxr-xr-x   4 root  root      4096 Nov 29 17:16 dconf
-rw-r--r--   1 root  root      2969 Aug 16 13:42 debconf.conf
-rw-r--r--   1 root  root        11 Jul  3  2012 debian_version
drwxr-xr-x   3 root  root      4096 Dec 26 07:39 default
-rw-r--r--   1 root  root       604 May  1  2012 deluser.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 depmod.d
drwxr-xr-x   4 root  root      4096 Dec 14 18:09 dhcp
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 dhcp3
drwxr-xr-x   2 root  root      4096 Nov 22 18:08 dictionaries-common
drwxr-xr-x   3 root  root      4096 Nov 28 20:47 dkms
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 dnsmasq.d
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 doc-base
drwxr-xr-x   4 root  root      4096 Nov 26 18:36 dpkg
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 emacs
-rw-r--r--   1 root  root        96 Oct 17 10:56 environment
drwxr-xr-x   2 root  root      4096 Nov 22 18:56 esound
drwxr-xr-x   3 root  root      4096 Dec 14 18:10 firefox
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 fonts
drwxr-xr-x   3 root  root      4096 Oct 17 10:59 foomatic
-rw-r--r--   1 root  root       635 Nov 22 18:03 fstab
drwxr-xr-x   2 root  root      4096 Sep  6 17:28 fstab.d
-rw-r-----   1 root  fuse       216 Oct 18  2011 fuse.conf
-rw-r--r--   1 root  root      3343 Oct  3 21:14 gai.conf
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 gconf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 gdb
drwxr-xr-x   6 root  root      4096 Nov 29 17:22 gdm
drwxr-xr-x   4 root  root      4096 Oct 17 10:58 ghostscript
drwxr-xr-x   3 root  root      4096 Nov 27 05:06 gimp
-rw-r--r--   1 root  root       580 Jul 16 00:05 gnashpluginrc
-rw-r--r--   1 root  root      5597 Jul 16 00:05 gnashrc
-rw-r--r--   1 root  root       690 Jul 16 00:05 gnashthumbnailrc
drwxr-xr-x   3 root  root      4096 Nov 29 17:17 gnome
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 gnome-app-install
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 gnome-settings-daemon
drwxr-xr-x   3 root  root      4096 Nov 27 02:42 gnome-vfs-2.0
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 groff
-rw-r--r--   1 root  root       998 Nov 29 17:23 group
-rw-------   1 root  root       978 Nov 29 17:22 group-
drwxr-xr-x   2 root  root      4096 Dec  7 07:45 grub.d
-rw-r-----   1 root  shadow     826 Nov 29 17:23 gshadow
-rw-------   1 root  root       809 Nov 29 17:22 gshadow-
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 gtk-2.0
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 gtk-3.0
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 gtkmathview
-rw-r--r--   1 root  root      4728 May  1  2012 hdparm.conf
-rw-r--r--   1 root  root        92 Jul  3  2012 host.conf
-rw-r--r--   1 root  root         4 Nov 22 18:06 hostname
-rw-r--r--   1 root  root       218 Nov 22 18:06 hosts
-rw-r--r--   1 root  root       594 Nov 28 01:04 hosts.allow
-rw-r--r--   1 root  root       880 Oct 17 10:59 hosts.deny
drwxr-xr-x   3 root  root      4096 Nov 29 17:17 hotplug
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 hp
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 ifplugd
drwxr-xr-x   2 root  root      4096 Nov 26 01:09 ImageMagick
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 init
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 init.d
drwxr-xr-x   3 root  root      4096 Dec 23 21:30 initramfs
drwxr-xr-x   5 root  root      4096 Oct 17 10:56 initramfs-tools
-rw-r--r--   1 root  root      1721 Sep 18 08:21 inputrc
drwxr-xr-x   3 root  root      4096 Aug 10 10:49 insserv
-rw-r--r--   1 root  root       839 Aug 10 10:49 insserv.conf
drwxr-xr-x   2 root  root      4096 Nov 29 17:22 insserv.conf.d
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 iproute2
-rw-r--r--   1 root  root        20 Oct  9 10:59 issue
-rw-r--r--   1 root  root        13 Oct  9 10:59 issue.net
drwxr-xr-x   3 root  root      4096 Dec  4 14:02 .java
drwxr-xr-x   2 root  root      4096 Dec  4 14:02 java-6-openjdk
drwxr-xr-x   5 root  root      4096 Dec  4 14:02 java-7-openjdk
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 kbd
drwxr-xr-x   6 root  root      4096 Nov 28 20:46 kernel
-rw-r--r--   1 root  root       110 Nov 22 18:09 kernel-img.conf
-rw-r--r--   1 root  root      1311 Jul 20 12:58 kerneloops.conf
lrwxrwxrwx   1 root  root         4 Sep 24 15:58 kvm -> qemu
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 ldap
-rw-r--r--   1 root  root    117489 Jan  1 18:47 ld.so.cache
-rw-r--r--   1 root  root        34 Oct 17 10:56 ld.so.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 ld.so.conf.d
-rw-r--r--   1 root  root       267 Jul  3  2012 legal
-rw-r--r--   1 root  root       191 Jan 15  2012 libaudit.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 libnl-3
drwxr-xr-x   2 root  root      4096 May 30  2012 libpaper.d
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 libreoffice
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 lightdm
-rw-r--r--   1 root  root      1291 Sep 28 12:38 lintianrc
-rw-r--r--   1 root  root      2570 Aug  5  2010 locale.alias
-rw-r--r--   1 root  root      3519 Nov 22 18:06 localtime
drwxr-xr-x   6 root  root      4096 Nov 28 01:04 logcheck
-rw-r--r--   1 root  root     10551 Sep  6 15:14 login.defs
-rw-r--r--   1 root  root       599 Oct  4  2011 logrotate.conf
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 logrotate.d
drwxr-xr-x   2 root  root      4096 Oct 10 14:31 lsb-base
-rw-r--r--   1 root  root      3279 Aug 14 22:17 lsb-base-logging.sh
-rw-r--r--   1 root  root       100 Oct  9 08:14 lsb-release
-rw-r--r--   1 root  root     15752 Jul 25  2009 ltrace.conf
-rw-r--r--   1 root  root       111 Jun 30  2012 magic
-rw-r--r--   1 root  root       111 Jun 30  2012 magic.mime
drwxr-sr-x   7 smmta smmsp     4096 Nov 29 17:21 mail
-rw-r--r--   1 root  root     29362 Dec 21 04:10 mailcap
-rw-r--r--   1 root  root       449 Jul 16 05:12 mailcap.order
-rw-r--r--   1 root  root      5173 Sep 18 18:44 manpath.config
drwxr-xr-x   2 root  root      4096 Nov 26 19:20 mc
drwxr-xr-x   2 root  root      4096 Nov 29 17:20 menu
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 menu-methods
drwxr-xr-x   3 root  root      4096 Nov 26 19:17 mercurial
-rw-r--r--   1 root  root     24269 Jul 16 05:12 mime.types
-rw-r--r--   1 root  root       956 Aug 22 18:33 mke2fs.conf
drwxr-xr-x   2 root  root      4096 Nov 28 20:47 modprobe.d
-rw-r--r--   1 root  root       203 Nov 22 18:08 modules
drwxr-xr-x   4 root  root      4096 Nov 29 17:23 mono
lrwxrwxrwx   1 root  root        13 Nov 22 18:01 motd -> /var/run/motd
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich2
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich-mpd
drwxr-xr-x   2 root  root      4096 Dec 20 20:16 mpich-shmem
drwxr-xr-x   2 root  root      4096 Nov 22 18:57 mplayer
-rw-r--r--   1 root  root       936 Jan  1 18:26 mtab
-rw-------   1 root  lightdm      0 Nov 22 18:26 mtab.fuselock
-rw-r--r--   1 root  root       624 Aug  8  2007 mtools.conf
-rw-r--r--   1 root  root      8453 Oct  1 10:11 nanorc
-rw-r--r--   1 root  root      2064 Nov 23  2006 netscsid.conf
drwxr-xr-x   6 root  root      4096 Oct 17 10:56 network
drwxr-xr-x   6 root  root      4096 Oct 17 11:00 NetworkManager
-rw-r--r--   1 root  root        91 Jul  3  2012 networks
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 newt
-rw-r--r--   1 root  root       513 Oct 17 11:00 nsswitch.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 obex-data-server
-rw-r--r--   1 root  root       109 Jun  8  2012 ocamlfind.conf
-rw-r--r--   1 root  root      1172 Sep  6 04:37 octave.conf
drwxr-xr-x   2 root  root      4096 Oct  8 19:26 ODBCDataSources
-rw-r--r--   1 root  root         0 Oct  8 19:26 odbc.ini
-rw-r--r--   1 root  root         0 Nov 26 01:09 odbcinst.ini
drwxr-xr-x   2 root  root      4096 Nov 22 18:12 openal
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 openvpn
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 opt
-rw-r--r--   1 root  root       128 Oct 23 17:53 os-release
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 PackageKit
-rw-r--r--   1 root  root       552 Jul  3  2012 pam.conf
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 pam.d
-rw-r--r--   1 root  root         7 Nov 22 18:08 papersize
-rw-r--r--   1 root  root      1911 Nov 29 17:23 passwd
-rw-------   1 root  root      1911 Nov 29 17:23 passwd-
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 pcmcia
drwxr-xr-x   4 root  root      4096 Oct 17 10:58 perl
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 pkcs11
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 pm
-rw-r--r--   1 root  root      7649 Oct 17 11:00 pnm2ppa.conf
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 polkit-1
-rw-r--r--   1 root  root       350 Nov 22 18:08 popularity-contest.conf
drwxr-xr-x   8 root  root      4096 Oct 17 11:00 ppp
lrwxrwxrwx   1 root  root        22 Dec 14 18:08 printcap -> /var/run/cups/printcap
-rw-r--r--   1 root  root       665 Dec 14 17:58 profile
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 profile.d
-rw-r--r--   1 root  root      2933 Jul  3  2012 protocols
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 pulse
-rw-------   1 root  root         0 Oct 17 10:56 .pwd.lock
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 python
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 python2.7
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 python3
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 python3.2
drwxr-xr-x   2 root  root      4096 Nov 28 02:34 qemu
lrwxrwxrwx   1 root  root        20 Sep 24 15:58 qemu-ifdown -> /usr/bin/qemu-ifdown
lrwxrwxrwx   1 root  root        18 Sep 24 15:58 qemu-ifup -> /usr/bin/qemu-ifup
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc0.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc1.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc2.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc3.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc4.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc5.d
drwxr-xr-x   2 root  root      4096 Dec 26 07:39 rc6.d
-rwxr-xr-x   1 root  root       306 Oct 17 10:56 rc.local
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 rcS.d
-rw-r--r--   1 root  root       121 Oct  4 05:41 remote-login-service.conf
-rw-r--r--   1 root  root      1889 Jun 30  2012 request-key.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:01 request-key.d
drwxr-xr-x   5 root  root      4096 Oct 17 10:58 resolvconf
lrwxrwxrwx   1 root  root        29 Nov 22 18:06 resolv.conf -> ../run/resolvconf/resolv.conf
-rwxr-xr-x   1 root  root       268 Mar 30  2012 rmt
-rw-r--r--   1 root  root       887 Jul  3  2012 rpc
-rw-r--r--   1 root  root      1263 Mar 30  2012 rsyslog.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 rsyslog.d
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 samba
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 sane.d
-rw-r--r--   1 root  root      3902 Sep  6 15:14 securetty
drwxr-xr-x   4 root  root      4096 Oct 17 11:00 security
-rw-r--r--   1 root  root     10333 Oct  5 07:36 sensors3.conf
drwxr-xr-x   2 root  root      4096 Oct 17 10:59 sensors.d
-rw-r--r--   1 root  root     19398 Jul  3  2012 services
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 sgml
-rw-r-----   1 root  shadow    1155 Nov 29 17:23 shadow
-rw-------   1 root  root      1155 Nov 29 17:23 shadow-
-rw-r--r--   1 root  root        84 Nov 22 18:58 shells
-rw-r--r--   1 root  root       657 Sep 19 15:08 signond.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:58 signon-ui
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 skel
-rw-r--r--   1 root  root      1132 Jun  8  2012 smi.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 snmp
drwxr-xr-x   3 root  root      4096 Nov 27 02:42 sound
drwxr-xr-x   3 root  root      4096 Nov 29 17:23 spamassassin
drwxr-xr-x   4 root  root      4096 Oct 17 11:00 speech-dispatcher
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 ssh
drwxr-xr-x   4 root  root      4096 Oct 17 10:59 ssl
drwxr-xr-x   2 root  root      4096 Nov 26 19:17 subversion
-r--r-----   1 root  root       745 Jul 16 08:13 sudoers
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 sudoers.d
-rw-r--r--   1 root  root        19 May  1  2011 su-to-rootrc
-rw-r--r--   1 root  root      2083 Nov 15  2011 sysctl.conf
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 sysctl.d
drwxr-xr-x   3 root  root      4096 Oct 17 10:56 systemd
drwxr-xr-x   2 root  root      4096 Oct 17 10:56 terminfo
drwxr-xr-x   3 root  root      4096 Nov 27 02:56 texmf
drwxr-xr-x   2 root  root      4096 Nov 22 18:08 thunderbird
-rw-r--r--   1 root  root        17 Nov 22 18:06 timezone
drwxr-xr-x   2 root  root      4096 Nov 22 18:13 timidity
-rw-r--r--   1 root  root       645 May  1  2012 ts.conf
-rw-r--r--   1 root  root      1260 May 30  2008 ucf.conf
drwxr-xr-x   3 root  root      4096 Oct 17 10:56 udev
drwxr-xr-x   2 root  root      4096 Oct  9 15:45 udisks2
drwxr-xr-x   3 root  root      4096 Oct 17 11:00 ufw
-rw-r--r--   1 root  root       326 Aug 14 23:26 updatedb.conf
drwxr-xr-x   3 root  root      4096 Dec 14 18:10 update-manager
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 update-motd.d
drwxr-xr-x   2 root  root      4096 Oct  9 18:41 update-notifier
-rw-r--r--   1 root  root        32 Oct  9  2011 upek.cfg
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 UPower
-rw-r--r--   1 root  root       572 Oct  8 22:08 usb_modeswitch.conf
drwxr-xr-x   2 root  root      4096 Sep 19 09:13 usb_modeswitch.d
-rw-r--r--   1 root  root        51 Jun 15  2012 vdpau_wrapper.cfg
drwxr-xr-x   2 root  root      4096 Nov 22 18:57 vga
drwxr-xr-x   2 root  root      4096 Dec 14 18:09 vim
drwxr-xr-x   3 root  root      4096 Nov 22 18:56 vlc
lrwxrwxrwx   1 root  root        23 Nov 22 18:01 vtrgb -> /etc/alternatives/vtrgb
-rw-r--r--   1 root  root      4496 Jun 14  2012 wgetrc
drwxr-xr-x   2 root  root      4096 Nov 22 18:12 wildmidi
drwxr-xr-x   2 root  root      4096 Dec 22 08:48 wireshark
-rw-r--r--   1 root  root      1343 Jan  9  2007 wodim.conf
drwxr-xr-x   2 root  root      4096 Oct 17 11:00 wpa_supplicant
drwxr-xr-x  10 root  root      4096 Nov 29 17:22 X11
drwxr-xr-x   5 root  root      4096 Oct 17 11:00 xdg
drwxr-xr-x   2 root  root      4096 Nov 29 17:23 xml
drwxr-xr-x   2 root  root      4096 Dec 14 18:10 xul-ext
-rw-r--r--   1 root  root       349 Jan 13  2012 zsh_command_not_found

```

---

### Post by SaronaSilverwolf on 2013-01-02
We ended up scrapping it and reinstalling the entire thing. Thanks for all of your help.

---

