---
title: "software-center bug"
date: 2014-12-02
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-12-02
Just today.

```

Processing triggers for dictionaries-common (1.23.17) ...
Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)
ventrical@ventrical-P5QL-PRO:~$ 

```


[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1398395](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1398395)

so I mee tooed it. :)

xubuntu seems to have a rather  more organized and elegant way of handling the bug reporting process. This is the first time I have seen apport behave in such an exemplary manner.

Regards..

---

### Post by slickymaster on 2014-12-02
Same here, on a 32 bit box.

```
....
Installing new version of config file /etc/dbus-1/system.d/org.freedesktop.machine1.conf ...
Installing new version of config file /etc/dbus-1/system.d/org.freedesktop.systemd1.conf ...
Installing new version of config file /etc/pam.d/systemd-user ...
Installing new version of config file /etc/systemd/logind.conf ...
Installing new version of config file /etc/systemd/resolved.conf ...
Installing new version of config file /etc/systemd/timesyncd.conf ...
Setting up libgudev-1.0-0:i386 (1:217-2ubuntu1) ...
Setting up libsystemd-daemon0:i386 (217-2ubuntu1) ...
Setting up libsystemd-login0:i386 (217-2ubuntu1) ...
Setting up libtdb1:i386 (1.3.2-1) ...
Setting up xfce4-session (4.11.1-0ubuntu1) ...
Installing new version of config file /etc/xdg/autostart/xscreensaver.desktop ...
Installing new version of config file /etc/xdg/xfce4/xinitrc ...
Setting up libapparmor-perl (2.8.98-0ubuntu4) ...
Setting up apparmor (2.8.98-0ubuntu4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Files /var/lib/dpkg/info/apparmor.md5sums and /var/lib/apparmor/profiles/.apparmor.md5sums differ
Setting up ppp (2.4.5-5.1ubuntu5) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up gir1.2-gudev-1.0 (1:217-2ubuntu1) ...
Setting up xfce4-power-manager-data (1.4.2-0ubuntu2) ...
Setting up xfce4-power-manager (1.4.2-0ubuntu2) ...
Setting up xfce4-power-manager-plugins (1.4.2-0ubuntu2) ...
Processing triggers for dbus (1.8.8-2ubuntu2) ...
Setting up libpam-systemd:i386 (217-2ubuntu1) ...
Setting up language-pack-en (1:15.04+20141201) ...
[COLOR=#ff0000]dpkg: cycle found while processing triggers:
 chain of packages whose triggers are or may be responsible:
  software-center -> software-center
 packages' pending triggers which are or may be unresolvable:
  software-center: /usr/share/locale-langpack
  shared-mime-info: /usr/share/mime/packages
  libc-bin: ldconfig
  initramfs-tools: update-initramfs
  gconf2: /usr/share/GConf/gsettings
dpkg: error processing package software-center (--configure):
 triggers looping, abandoned[/COLOR]
....
Processing triggers for libc-bin (2.19-13ubuntu2) ...
Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-25-generic
Errors were encountered while processing:
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by slickymaster on 2014-12-02
Running **sudo apt-get install -f **seemed to resolve it:```
~$ sudo apt-get install -f
[sudo] password for slickymaster: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Setting up software-center (13.10-0ubuntu4.1) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
slickymaster@VirtualBox:~$ 

```

---

### Post by ventrical on 2014-12-02
Will do.

Yep..

```

ventrical@ventrical-P5QL-PRO:~$ sudo apt-get install -f
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  docutils-common docutils-doc linux-headers-3.16.0-22
  linux-headers-3.16.0-22-generic linux-image-3.16.0-22-generic
  linux-image-extra-3.16.0-22-generic python-docutils python-pygments
  python-roman
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Setting up software-center (13.10-0ubuntu4.1) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
ventrical@ventrical-P5QL-PRO:~$ 



```

 Strange then that it would report a bug.

---

### Post by slickymaster on 2014-12-02
> **ventrical said:**
> Will do.

Yep..

```

ventrical@ventrical-P5QL-PRO:~$ sudo apt-get install -f
[sudo] password for ventrical: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  docutils-common docutils-doc linux-headers-3.16.0-22
  linux-headers-3.16.0-22-generic linux-image-3.16.0-22-generic
  linux-image-extra-3.16.0-22-generic python-docutils python-pygments
  python-roman
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Processing triggers for gconf2 (3.2.6-3ubuntu1) ...
Setting up software-center (13.10-0ubuntu4.1) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
ventrical@ventrical-P5QL-PRO:~$ 



```

 Strange then that it would report a bug.

Indeed, was thinking about it myself. :confused:

---

