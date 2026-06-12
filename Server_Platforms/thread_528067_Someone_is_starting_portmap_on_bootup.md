---
title: "Someone is starting portmap on bootup"
date: 2007-08-17
forum: Server Platforms
---

### Post by ihristov on 2007-08-17
I installed the package nfs-user-server. I used it and then want to make it not start automatically on bootup.

To that end I removed the shortcut in rc2.d folder - /etc/rd2.d/S25nfs-user-server

However after startup I still see that the portmap service is started and listening on port 111

```
$ sudo netstat -natp | grep LISTEN | grep -v 127.0.0.1
tcp        0      0 0.0.0.0:902             0.0.0.0:*               LISTEN     7176/inetd          
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     8299/portmap        
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     5704/sshd
```

Who is starting this, so I can disable it?

I do not have a startup shortcut for it in /etc/rc2.d/. In fact here is the list of the services that are started automatically

```
$ ls -l /etc/rc2.d/S*
lrwxrwxrwx 1 root root 17 2007-06-02 03:27 /etc/rc2.d/S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root 15 2007-06-02 03:27 /etc/rc2.d/S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root 25 2007-06-02 03:27 /etc/rc2.d/S10powernowd.early -> ../init.d/powernowd.early
lrwxrwxrwx 1 root root 18 2007-06-02 03:27 /etc/rc2.d/S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root 15 2007-06-02 03:27 /etc/rc2.d/S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root 14 2007-06-02 03:27 /etc/rc2.d/S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root 13 2007-06-02 03:27 /etc/rc2.d/S13gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root 17 2007-06-04 21:36 /etc/rc2.d/S16openvpn -> ../init.d/openvpn
lrwxrwxrwx 1 root root 16 2007-06-02 03:27 /etc/rc2.d/S19cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root 16 2007-06-02 03:27 /etc/rc2.d/S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root 22 2007-06-30 15:53 /etc/rc2.d/S20cpufrequtils -> ../init.d/cpufrequtils
lrwxrwxrwx 1 root root 17 2007-07-05 10:14 /etc/rc2.d/S20hddtemp -> ../init.d/hddtemp
lrwxrwxrwx 1 root root 22 2007-06-02 03:27 /etc/rc2.d/S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root 15 2007-06-03 21:40 /etc/rc2.d/S20inetd -> ../init.d/inetd
lrwxrwxrwx 1 root root 17 2007-06-02 03:27 /etc/rc2.d/S20makedev -> ../init.d/makedev
lrwxrwxrwx 1 root root 23 2007-06-02 03:27 /etc/rc2.d/S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root 19 2007-06-02 03:27 /etc/rc2.d/S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root 15 2007-06-02 03:27 /etc/rc2.d/S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root 13 2007-07-13 07:38 /etc/rc2.d/S20ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root 17 2007-06-06 13:27 /etc/rc2.d/S20sysstat -> ../init.d/sysstat
lrwxrwxrwx 1 root root 17 2007-07-01 19:53 /etc/rc2.d/S20vboxdrv -> ../init.d/vboxdrv
lrwxrwxrwx 1 root root 19 2007-06-02 03:27 /etc/rc2.d/S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root 13 2007-06-08 05:22 /etc/rc2.d/S50ntp -> ../init.d/ntp
lrwxrwxrwx 1 root root 17 2007-06-02 03:27 /etc/rc2.d/S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root 13 2007-06-02 03:27 /etc/rc2.d/S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root 14 2007-06-02 03:27 /etc/rc2.d/S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root 24 2007-06-02 03:27 /etc/rc2.d/S90binfmt-support -> ../init.d/binfmt-support
lrwxrwxrwx 1 root root 17 2007-06-02 03:27 /etc/rc2.d/S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root 22 2007-06-02 03:27 /etc/rc2.d/S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root 18 2007-06-02 03:27 /etc/rc2.d/S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root 19 2007-06-02 03:27 /etc/rc2.d/S99rmnologin -> ../init.d/rmnologin
lrwxrwxrwx 1 root root 24 2007-06-02 03:27 /etc/rc2.d/S99stop-readahead -> ../init.d/stop-readahead

```

---

### Post by HermanAB on 2007-08-18
Portmap is used by the Sun protocols: NFS, NIS and so on.

System -> Administration -> Services option, there's a services admin tool.

You can also use 
$ sudo service portmap stop

and
$ sudo chkconfig --list portmap

then something like
$ sudo chkconfig portmap --level 35 off

Cheers,

Herman

---

### Post by ihristov on 2007-08-19
I do not have the chkconfig utility installed. What package does it come from?

Using "services-admin" did not fix it. It creates and deletes a link in /etc/rc2.d/ as could be expected.

It appears the problems is in the /etc/rcS.d/ folder where these services are started for any level
I removed /etc/rcS.d/S43portmap and all should be dandy now.

Thanks.

```
$ ls -l /etc/rc?.d/*portmap*
lrwxrwxrwx 1 root root 17 2007-07-09 19:51 /etc/rc0.d/K32portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root 17 2007-07-09 19:51 /etc/rc1.d/K81portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root 17 2007-07-09 19:51 /etc/rc3.d/K18portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root 17 2007-07-09 19:51 /etc/rc4.d/K18portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root 17 2007-07-09 19:51 /etc/rc5.d/K18portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root 17 2007-07-09 19:51 /etc/rc6.d/K32portmap -> ../init.d/portmap
lrwxrwxrwx 1 root root 17 2007-07-09 19:51 /etc/rcS.d/S43portmap -> ../init.d/portmap
```

---

