---
title: "Problem on upgrade: version `XCRYPT_2.0' not found"
date: 2020-03-14
forum: Ubuntu Development Version
---

### Post by rakeshshrs on 2020-03-14
I got upgrade notification. After upgrade command, I get following errors:
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)

```
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
Setting up mime-support (3.64ubuntu1) ...
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
dpkg: error processing package mime-support (--configure):
 installed mime-support package post-installation script subprocess returned error exit status 1
Setting up initramfs-tools (0.136ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Setting up plymouth (0.9.4git20200109-0ubuntu8) ...
update-initramfs: deferring update (trigger activated)
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
dpkg: error processing package plymouth (--configure):
 installed plymouth package post-installation script subprocess returned error exit status 1
Setting up network-manager (1.22.10-1ubuntu1) ...
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
dpkg: error processing package network-manager (--configure):
 installed network-manager package post-installation script subprocess returned error exit status 1
Setting up kmod (27-1ubuntu2) ...
update-initramfs: deferring update (trigger activated)
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
dpkg: error processing package kmod (--configure):
 installed kmod package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up grub-common (2.04-1ubuntu22) ...
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
dpkg: error processing package grub-common (--configure):
 installed grub-common package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up unattended-upgrades (2.0) ...
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
dpkg: error processing package unattended-upgrades (--configure):
 installed unattended-upgrades package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-themes:
 plymouth-themes depends on plymouth (= 0.9.4git20200109-0ubuntu8); however:
  Package plymouth is not configured yet.


dpkg: error processing package plymouth-themes (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-theme-spinner:
 plymouth-theme-spinner depends on plymouth (= 0.9.4git20200109-0ubuntu8); however:
  Package plymouth is not configured yet.


dpkg: error processing package plymouth-theme-spinner (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.9.4git20200109-0ubuntu8); however:
  Package plymouth is not configured yet.


dpkg: error processing package plymouth-label (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of network-manager-openvpn:
 network-manager-openvpn depends on network-manager (>= 1.2.0); however:
  Package network-manager is not configured yet.


dpkg: error processing package network-manager-openvpn (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on kmod; however:
  Package kmod is not configured yet.


dpkg: error processing package ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 2.04-1ubuntu22); however:
  Package grub-common is not configured yet.


dpkg: error processing package grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-openconnect:
 network-manager-openconnect depends on network-manager (>= 1.2); however:
  Package network-manager is not configured yet.


No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: error processing package network-manager-openconnect (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-config-connectivity-ubuntu:
 network-manager-config-connectivity-ubuntu depends on network-manager (>= 1.22.10-1ubuntu1); however:
  Package network-manager is not configured yet.


dpkg: error processing package network-manager-config-connectivity-ubuntu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of network-manager-openvpn-gnome:
 network-manager-openvpn-gnome depends on network-manager-openvpn (= 1.8.12-1); however:
  Package network-manager-openvpn is not configured yet.


dpkg: error processing package network-manager-openvpn-gnome (--configure):No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already


 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on grub-common (= 2.04-1ubuntu22); however:
  Package grub-common is not configured yet.


dpkg: error processing package grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common (= 2.04-1ubuntu22); however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 2.04-1ubuntu22); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 2.04-1ubuntu22); however:
  Package grub-pc-bin is not configured yet.


dpkg: error processing package grub-pc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of network-manager-openconnect-gnome:
 network-manager-openconnect-gnome depends on network-manager-openconnect (= 1.2.4-4); however:
  Package network-manager-openconnect is not configured yet.


dpkg: error processing package network-manager-openconnect-gnome (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for initramfs-tools (0.136ubuntu1) ...
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
/usr/bin/perl: /lib/x86_64-linux-gnu/libcrypt.so.1: version `XCRYPT_2.0' not found (required by /usr/bin/perl)
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 mime-support
 plymouth
 network-manager
 kmod
 grub-common
 unattended-upgrades
 plymouth-themes
 plymouth-theme-spinner
 plymouth-label
 network-manager-openvpn
 ubuntu-minimal
 grub2-common
 network-manager-openconnect
 network-manager-config-connectivity-ubuntu
 network-manager-openvpn-gnome
 grub-pc-bin
 grub-pc
 network-manager-openconnect-gnome
 initramfs-tools



```

---

### Post by tokyobadger on 2020-03-15
You seem to have been affected around the same time as me, hence no grub/log-in drama.

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
sudo apt-get install -f
```

Fixed it.

[bug at launchpad](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/1867431)

---

