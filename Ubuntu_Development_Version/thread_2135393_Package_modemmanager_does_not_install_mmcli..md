---
title: "Package modemmanager does not install mmcli."
date: 2013-04-14
forum: Ubuntu Development Version
---

### Post by BhimaPandava on 2013-04-14
I have headless server running 13.04, uname -r: 3.8.0-17-generic, which needs to use 3G modems to connect to the internet from the field.  So I have been trying to use Network-Manager & modmemmanager from the command line.

I have found that installing the modmemmanager using apt-get doesn't also install mmcli.  Building it from source forces me to also install an array of unneeded dependancies (for the GUI parts) and results in an mmcli which doesn't apear to play well with my system's dbus daemon.

At this point, I'm sort of stuck and I think I need mmcli to proceed.

---

### Post by serdotlinecho on 2013-04-15
Do you have network-manager installed?

```
root@lokalhost:~# dpkg -S network-manager
network-manager: /etc/init.d/network-manager
network-manager-pptp: /usr/share/doc/network-manager-pptp/README
network-manager: /usr/share/doc/network-manager/README.Debian
network-manager: /usr/share/doc/network-manager/NEWS.Debian.gz
network-manager-gnome: /usr/share/doc/network-manager-gnome/NEWS.gz
network-manager-gnome: /usr/share/doc/network-manager-gnome/copyright
app-install-data: /usr/share/app-install/desktop/network-manager-gnome:nm-applet.desktop
network-manager-pptp-gnome: /usr/share/doc/network-manager-pptp-gnome/changelog.Debian.gz
network-manager: /usr/share/doc/network-manager/copyright
network-manager-pptp: /usr/share/doc/network-manager-pptp
network-manager: /etc/init/network-manager.conf
network-manager: /usr/share/doc/network-manager/README.gz
network-manager-gnome: /usr/share/doc/network-manager-gnome/README.Debian
network-manager: /usr/share/doc/network-manager
network-manager: /etc/dnsmasq.d/network-manager
network-manager-pptp: /usr/share/doc/network-manager-pptp/NEWS.gz
network-manager-gnome: /usr/share/doc/network-manager-gnome
network-manager: /usr/share/doc/network-manager/changelog.Debian.gz
network-manager-pptp: /usr/share/doc/network-manager-pptp/AUTHORS
network-manager-gnome: /usr/share/doc/network-manager-gnome/changelog.Debian.gz
network-manager-pptp: /usr/share/doc/network-manager-pptp/changelog.Debian.gz
network-manager: /usr/share/apport/package-hooks/source_network-manager-applet.py
network-manager: /usr/share/apport/package-hooks/source_network-manager.py
network-manager: /usr/share/doc/network-manager/NEWS.gz
network-manager: /usr/share/doc/network-manager/AUTHORS
network-manager-pptp-gnome: /usr/share/doc/network-manager-pptp-gnome
network-manager-pptp-gnome: /usr/share/doc/network-manager-pptp-gnome/copyright
network-manager-pptp: /usr/share/doc/network-manager-pptp/copyright
root@lokalhost:~# dpkg -S nmcli
network-manager: /usr/share/man/man1/nmcli.1.gz
network-manager: /usr/share/bash-completion/completions/nmcli
network-manager: /usr/bin/nmcli
```

---

### Post by ben24 on 2013-09-19
This is for nmcli, not mmcli.  I've got the same conundrum just now...  :)

---

