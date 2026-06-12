---
title: "How can I check security on my computer?"
date: 2017-11-15
forum: Security
---

### Post by mollie4168 on 2017-11-15
I'm realizing that my OS has not been regularly updating, and when I try to install the updates through the Software Center, it doesn't seem to do anything.   How can I check whether security (and everything else) is up to date?    Thanks.

---

### Post by howefield on 2017-11-15
You could try updating from a terminal...

```
sudo apt update
```
```
sudo apt upgrade
```

and post back here the output.

---

### Post by mollie4168 on 2018-03-17
See next post.

---

### Post by mollie4168 on 2018-03-17
I'm aware that I should have been following up on this sooner.  From what I see, I'm concerned about that last line, that it can't fetch some of the packages.  Also, I'll uninstall skype since it's causing problems.


```
tracy@ubuntu:~$ sudo apt update
[sudo] password for tracy: 
Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu xenial-security InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease      
Ign:5 http://dl.google.com/linux/musicmanager/deb stable InRelease      
Hit:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:7 http://dl.google.com/linux/chrome/deb stable Release
Get:8 https://repo.skype.com/deb stable InRelease [4,486 B]
Hit:9 http://dl.google.com/linux/musicmanager/deb stable Release               
Hit:10 https://s3.amazonaws.com/files.republicwireless.com/public/apps/anywhere/debian main InRelease
Err:8 https://repo.skype.com/deb stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
Reading package lists... Done 
W: GPG error: https://repo.skype.com/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
E: The repository 'https://repo.skype.com/deb stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
tracy@ubuntu:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libllvm3.8 libqmi-glib1 linux-headers-4.4.0-101
  linux-headers-4.4.0-101-generic linux-headers-4.4.0-103
  linux-headers-4.4.0-103-generic linux-headers-4.4.0-104
  linux-headers-4.4.0-104-generic linux-headers-4.4.0-109
  linux-headers-4.4.0-109-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-headers-4.4.0-77
  linux-headers-4.4.0-77-generic linux-headers-4.4.0-78
  linux-headers-4.4.0-78-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-headers-4.4.0-92
  linux-headers-4.4.0-92-generic linux-headers-4.4.0-93
  linux-headers-4.4.0-93-generic linux-headers-4.4.0-96
  linux-headers-4.4.0-96-generic linux-headers-4.4.0-97
  linux-headers-4.4.0-97-generic linux-headers-4.4.0-98
  linux-headers-4.4.0-98-generic linux-image-4.4.0-101-generic
  linux-image-4.4.0-103-generic linux-image-4.4.0-104-generic
  linux-image-4.4.0-109-generic linux-image-4.4.0-66-generic
  linux-image-4.4.0-70-generic linux-image-4.4.0-71-generic
  linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic
  linux-image-4.4.0-77-generic linux-image-4.4.0-78-generic
  linux-image-4.4.0-79-generic linux-image-4.4.0-81-generic
  linux-image-4.4.0-83-generic linux-image-4.4.0-87-generic
  linux-image-4.4.0-89-generic linux-image-4.4.0-92-generic
  linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-4.4.0-97-generic linux-image-4.4.0-98-generic
  linux-image-extra-4.4.0-101-generic linux-image-extra-4.4.0-103-generic
  linux-image-extra-4.4.0-104-generic linux-image-extra-4.4.0-109-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-70-generic
  linux-image-extra-4.4.0-71-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-75-generic linux-image-extra-4.4.0-77-generic
  linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-79-generic
  linux-image-extra-4.4.0-81-generic linux-image-extra-4.4.0-83-generic
  linux-image-extra-4.4.0-87-generic linux-image-extra-4.4.0-89-generic
  linux-image-extra-4.4.0-92-generic linux-image-extra-4.4.0-93-generic
  linux-image-extra-4.4.0-96-generic linux-image-extra-4.4.0-97-generic
  linux-image-extra-4.4.0-98-generic snap-confine ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following NEW packages will be installed:
  libdrm-common libinput-bin libllvm5.0 libqmi-glib5
The following packages will be upgraded:
  apparmor apparmor-profiles apt apt-transport-https apt-utils bamfdaemon
  base-files bsdutils compiz compiz-core compiz-gnome compiz-plugins-default
  coreutils cracklib-runtime cryptsetup cryptsetup-bin curl distro-info-data
  dnsmasq-base dpkg dpkg-dev firefox firefox-locale-en friendly-recovery fwupd
  fwupdate fwupdate-signed gir1.2-packagekitglib-1.0 gir1.2-unity-5.0
  gnome-accessibility-themes gnome-disk-utility gnome-software
  gnome-software-common google-chrome-stable grub-common grub-pc grub-pc-bin
  grub2-common gtk2-engines-pixbuf gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs initramfs-tools initramfs-tools-bin
  initramfs-tools-core iproute2 isc-dhcp-client isc-dhcp-common klibc-utils
  kmod less libapparmor-perl libapparmor1 libappstream-glib8 libapt-inst2.0
  libapt-pkg5.0 libaudit-common libaudit1 libbamf3-2 libblkid1
  libcompizconfig0 libcrack2 libcryptsetup4 libcurl3 libcurl3-gnutls
  libdecoration0 libdfu1 libdpkg-perl libdrm-amdgpu1 libdrm-intel1
  libdrm-nouveau2 libdrm-radeon1 libdrm2 libegl1-mesa libepoxy0 libfdisk1
  libfwup0 libfwupd1 libgail-common libgail18 libgbm1 libgcrypt20
  libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgnutls-openssl27
  libgnutls30 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgweather-3-6
  libgweather-common libinput10 libklibc libkmod2 libmbim-glib4 libmbim-proxy
  libmm-glib0 libmount1 libnautilus-extension1a libnm-glib-vpn1 libnm-glib4
  libnm-gtk-common libnm-gtk0 libnm-util2 libnm0 libnma-common libnma0
  libnuma1 libnux-4.0-0 libnux-4.0-common libpackagekit-glib2-16
  libparted-fs-resize0 libparted2 libplymouth4 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libpython-stdlib libpython2.7 libpython2.7-minimal
  libpython2.7-stdlib libqmi-proxy libqt5core5a libqt5dbus5 libqt5gui5
  libqt5network5 libqt5opengl5 libqt5printsupport5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5widgets5 libqt5xml5 libseccomp2
  libsmartcols1 libsnapd-glib1 libsnmp-base libsnmp30 libunity-control-center1
  libunity-core-6.0-9 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity9 libuuid1 libva1 libwacom-bin
  libwacom-common libwacom2 libwayland-egl1-mesa libwhoopsie0 libxatracker2
  light-themes linux-firmware logrotate lshw mesa-vdpau-drivers modemmanager
  mount nautilus-data network-manager network-manager-gnome nux-tools parted
  plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-x11 pulseaudio-utils python python-apt-common
  python-minimal python2.7 python2.7-minimal python3-apt python3-distupgrade
  republicanywhere resolvconf session-shortcuts skypeforlinux snap-confine
  snapd snapd-login-service squashfs-tools sudo suru-icon-theme ubuntu-artwork
  ubuntu-core-launcher ubuntu-desktop ubuntu-minimal ubuntu-mobile-icons
  ubuntu-mono ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  ubuntu-software ubuntu-standard unattended-upgrades unity
  unity-control-center unity-control-center-faces unity-schemas
  unity-scopes-runner unity-services update-notifier update-notifier-common
  util-linux uuid-runtime va-driver-all whoopsie xfonts-utils zlib1g
218 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 358 MB of archives.
After this operation, 175 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  skypeforlinux
Install these packages without verification? [y/N] y
Get:1 http://dl.google.com/linux/chrome/deb stable/main amd64 google-chrome-stable amd64 65.0.3325.162-1 [52.1 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 base-files amd64 9.4ubuntu4.6 [55.0 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 bsdutils amd64 1:2.27.1-6ubuntu3.4 [51.5 kB]
Get:4 https://repo.skype.com/deb stable/main amd64 skypeforlinux amd64 8.17.0.2 [72.2 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 coreutils amd64 8.25-2ubuntu3~16.04 [1,174 kB]
Get:6 https://s3.amazonaws.com/files.republicwireless.com/public/apps/anywhere/debian main/main amd64 republicanywhere amd64 1.5.8 [47.5 MB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 dpkg amd64 1.18.4ubuntu1.4 [2,088 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 util-linux amd64 2.27.1-6ubuntu3.4 [849 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 mount amd64 2.27.1-6ubuntu3.4 [121 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 zlib1g amd64 1:1.2.8.dfsg-2ubuntu4.1 [51.2 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapt-pkg5.0 amd64 1.2.25 [706 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapt-inst2.0 amd64 1.2.25 [55.5 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt amd64 1.2.25 [1,041 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt-utils amd64 1.2.25 [196 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 uuid-runtime amd64 2.27.1-6ubuntu3.4 [26.1 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-pc amd64 2.02~beta2-36ubuntu3.17 [197 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-pc-bin amd64 2.02~beta2-36ubuntu3.17 [888 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub2-common amd64 2.02~beta2-36ubuntu3.17 [511 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.17 [1,705 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython2.7 amd64 2.7.12-1ubuntu0~16.04.3 [1,070 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python2.7 amd64 2.7.12-1ubuntu0~16.04.3 [224 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython2.7-stdlib amd64 2.7.12-1ubuntu0~16.04.3 [1,880 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python2.7-minimal amd64 2.7.12-1ubuntu0~16.04.3 [1,261 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython2.7-minimal amd64 2.7.12-1ubuntu0~16.04.3 [340 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python-minimal amd64 2.7.12-1~16.04 [28.1 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python amd64 2.7.12-1~16.04 [137 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpython-stdlib amd64 2.7.12-1~16.04 [7,768 B]
Get:28 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-core-launcher amd64 2.29.4.2 [1,566 B]
Get:29 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snapd amd64 2.29.4.2 [13.0 MB]
Get:30 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snap-confine amd64 2.29.4.2 [1,720 B]
Get:31 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapparmor1 amd64 2.10.95-0ubuntu2.9 [29.9 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapparmor-perl amd64 2.10.95-0ubuntu2.9 [31.5 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apparmor amd64 2.10.95-0ubuntu2.9 [450 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 squashfs-tools amd64 1:4.3-3ubuntu2.16.04.1 [104 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python-apt-common all 1.1.0~beta1ubuntu0.16.04.1 [16.0 kB]
Get:36 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-apt amd64 1.1.0~beta1ubuntu0.16.04.1 [137 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-release-upgrader-gtk all 1:16.04.24 [9,302 B]
Get:38 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-release-upgrader-core all 1:16.04.24 [29.6 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 python3-distupgrade all 1:16.04.24 [104 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 update-notifier amd64 3.168.8 [47.3 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 update-notifier-common all 3.168.8 [164 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcurl3 amd64 7.47.0-1ubuntu2.7 [187 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgcrypt20 amd64 1.6.5-2ubuntu0.4 [337 kB]
Get:44 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 whoopsie amd64 0.2.52.5 [22.7 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwhoopsie0 amd64 0.2.52.5 [9,582 B]
Get:46 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libaudit-common all 1:2.4.5-1ubuntu2.1 [3,924 B]
Get:47 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libaudit1 amd64 1:2.4.5-1ubuntu2.1 [36.2 kB]
Get:48 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libuuid1 amd64 2.27.1-6ubuntu3.4 [15.2 kB]
Get:49 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libblkid1 amd64 2.27.1-6ubuntu3.4 [107 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcryptsetup4 amd64 2:1.6.6-5ubuntu2.1 [73.3 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libfdisk1 amd64 2.27.1-6ubuntu3.4 [139 kB]
Get:52 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 kmod amd64 22-1ubuntu5 [88.6 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libkmod2 amd64 22-1ubuntu5 [39.9 kB]
Get:54 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libmount1 amd64 2.27.1-6ubuntu3.4 [114 kB]
Get:55 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libseccomp2 amd64 2.3.1-2.1ubuntu2~16.04.1 [38.7 kB]
Get:56 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsmartcols1 amd64 2.27.1-6ubuntu3.4 [62.8 kB]
Get:57 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 distro-info-data all 0.28ubuntu0.7 [4,334 B]
Get:58 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 klibc-utils amd64 2.0.4-8ubuntu1.16.04.4 [108 kB]
Get:59 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 friendly-recovery all 0.2.31ubuntu1 [9,496 B]
Get:60 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 initramfs-tools all 0.122ubuntu8.10 [8,596 B]
Get:61 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 initramfs-tools-core all 0.122ubuntu8.10 [42.8 kB]
Get:62 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 initramfs-tools-bin amd64 0.122ubuntu8.10 [9,554 B]
Get:63 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libklibc amd64 2.0.4-8ubuntu1.16.04.4 [41.0 kB]
Get:64 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 iproute2 amd64 4.3.0-1ubuntu3.16.04.3 [522 kB]
Get:65 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 isc-dhcp-client amd64 4.3.3-5ubuntu12.10 [224 kB]
Get:66 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 isc-dhcp-common amd64 4.3.3-5ubuntu12.10 [105 kB]
Get:67 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 less amd64 481-2.1ubuntu0.2 [110 kB]
Get:68 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgnutls-openssl27 amd64 3.4.10-4ubuntu1.4 [22.0 kB]
Get:69 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgnutls30 amd64 3.4.10-4ubuntu1.4 [548 kB]
Get:70 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 logrotate amd64 3.8.7-2ubuntu2.16.04.2 [37.7 kB]
Get:71 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 resolvconf all 1.78ubuntu6 [51.8 kB]
Get:72 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 sudo amd64 1.8.16-0ubuntu1.5 [390 kB]
Get:73 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-minimal amd64 1.361.1 [2,540 B]
Get:74 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 curl amd64 7.47.0-1ubuntu2.7 [138 kB]
Get:75 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcurl3-gnutls amd64 7.47.0-1ubuntu2.7 [185 kB]
Get:76 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt-transport-https amd64 1.2.25 [26.1 kB]
Get:77 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdrm-common all 2.4.83-1~16.04.1 [4,870 B]
Get:78 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdrm2 amd64 2.4.83-1~16.04.1 [30.4 kB]
Get:79 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnuma1 amd64 2.0.11-1ubuntu1.1 [21.0 kB]
Get:80 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 parted amd64 3.2-15ubuntu0.1 [42.4 kB]
Get:81 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libparted-fs-resize0 amd64 3.2-15ubuntu0.1 [46.4 kB]
Get:82 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libparted2 amd64 3.2-15ubuntu0.1 [115 kB]
Get:83 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libplymouth4 amd64 0.9.2-3ubuntu13.2 [85.1 kB]
Get:84 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 lshw amd64 02.17-1.1ubuntu3.4 [216 kB]
Get:85 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 plymouth-theme-ubuntu-text amd64 0.9.2-3ubuntu13.2 [9,094 B]
Get:86 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 plymouth amd64 0.9.2-3ubuntu13.2 [107 kB]
Get:87 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 plymouth-theme-ubuntu-logo amd64 0.9.2-3ubuntu13.2 [22.2 kB]
Get:88 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 plymouth-label amd64 0.9.2-3ubuntu13.2 [6,092 B]
Get:89 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-standard amd64 1.361.1 [2,608 B]
Get:90 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 bamfdaemon amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1 [82.2 kB]
Get:91 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libbamf3-2 amd64 0.5.3~bzr0+16.04.20180209-0ubuntu1 [51.8 kB]
Get:92 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgl1-mesa-glx amd64 17.2.8-0ubuntu0~16.04.1 [130 kB]
Get:93 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libglapi-mesa amd64 17.2.8-0ubuntu0~16.04.1 [22.8 kB]
Get:94 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwayland-egl1-mesa amd64 17.2.8-0ubuntu0~16.04.1 [5,872 B]
Get:95 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libegl1-mesa amd64 17.2.8-0ubuntu0~16.04.1 [84.8 kB]
Get:96 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgbm1 amd64 17.2.8-0ubuntu0~16.04.1 [24.6 kB]
Get:97 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdrm-amdgpu1 amd64 2.4.83-1~16.04.1 [18.6 kB]
Get:98 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdrm-intel1 amd64 2.4.83-1~16.04.1 [59.9 kB]
Get:99 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdrm-nouveau2 amd64 2.4.83-1~16.04.1 [16.3 kB]
Get:100 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdrm-radeon1 amd64 2.4.83-1~16.04.1 [21.5 kB]
Get:101 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libllvm5.0 amd64 1:5.0-3~16.04.1 [13.5 MB]
Get:102 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgl1-mesa-dri amd64 17.2.8-0ubuntu0~16.04.1 [5,782 kB]
Get:103 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-util2 amd64 1.2.6-0ubuntu0.16.04.2 [126 kB]
Get:104 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-glib4 amd64 1.2.6-0ubuntu0.16.04.2 [84.2 kB]
Err:104 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-glib4 amd64 1.2.6-0ubuntu0.16.04.2
  Connection timed out [IP: 2001:67c:1562::16 80]
Get:105 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-gtk0 amd64 1.2.6-0ubuntu0.16.04.4 [70.3 kB]
Get:106 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-gtk-common all 1.2.6-0ubuntu0.16.04.4 [5,694 B]
Get:107 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpulsedsp amd64 1:8.0-0ubuntu3.8 [21.1 kB]
Get:108 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 pulseaudio-utils amd64 1:8.0-0ubuntu3.8 [51.0 kB]
Get:109 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 pulseaudio-module-x11 amd64 1:8.0-0ubuntu3.8 [16.0 kB]
Get:110 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 pulseaudio-module-bluetooth amd64 1:8.0-0ubuntu3.8 [58.6 kB]
Get:111 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 pulseaudio amd64 1:8.0-0ubuntu3.8 [766 kB]
Get:112 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpulse-mainloop-glib0 amd64 1:8.0-0ubuntu3.8 [11.5 kB]
Get:113 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpulse0 amd64 1:8.0-0ubuntu3.8 [249 kB]
Get:114 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity-control-center1 amd64 15.04.0+16.04.20171130-0ubuntu1 [81.1 kB]
Get:115 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwacom2 amd64 0.22-1~ubuntu16.04.1 [17.3 kB]
Get:116 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwacom-common all 0.22-1~ubuntu16.04.1 [32.0 kB]
Get:117 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity-control-center amd64 15.04.0+16.04.20171130-0ubuntu1 [835 kB]
Get:118 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcompizconfig0 amd64 1:0.9.12.3+16.04.20180221-0ubuntu1 [118 kB]
Get:119 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 compiz-gnome amd64 1:0.9.12.3+16.04.20180221-0ubuntu1 [127 kB]
Get:120 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 compiz-plugins-default amd64 1:0.9.12.3+16.04.20180221-0ubuntu1 [821 kB]
Get:121 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdecoration0 amd64 1:0.9.12.3+16.04.20180221-0ubuntu1 [51.9 kB]
Get:122 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libappstream-glib8 amd64 0.5.13-1ubuntu5 [101 kB]
Get:123 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnux-4.0-0 amd64 4.0.8+16.04.20170816-0ubuntu1 [697 kB]
Get:124 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnux-4.0-common all 4.0.8+16.04.20170816-0ubuntu1 [42.0 kB]
Get:125 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity amd64 7.4.5+16.04.20180221-0ubuntu1 [1,619 kB]
Get:126 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity-protocol-private0 amd64 7.1.4+16.04.20180209.1-0ubuntu1 [78.7 kB]
Get:127 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity9 amd64 7.1.4+16.04.20180209.1-0ubuntu1 [199 kB]
Get:128 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity-core-6.0-9 amd64 7.4.5+16.04.20180221-0ubuntu1 [437 kB]
Get:129 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity-schemas all 7.4.5+16.04.20180221-0ubuntu1 [12.9 kB]
Get:130 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity-scopes-json-def-desktop all 7.1.4+16.04.20180209.1-0ubuntu1 [3,548 B]
Get:131 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity-services amd64 7.4.5+16.04.20180221-0ubuntu1 [33.4 kB]
Get:132 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 nux-tools amd64 4.0.8+16.04.20170816-0ubuntu1 [9,954 B]
Get:133 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 compiz-core amd64 1:0.9.12.3+16.04.20180221-0ubuntu1 [348 kB]
Get:134 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 compiz all 1:0.9.12.3+16.04.20180221-0ubuntu1 [3,860 B]
Get:135 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libcrack2 amd64 2.9.2-1ubuntu1 [28.2 kB]
Get:136 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cracklib-runtime amd64 2.9.2-1ubuntu1 [134 kB]
Get:137 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cryptsetup-bin amd64 2:1.6.6-5ubuntu2.1 [61.8 kB]
Get:138 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 cryptsetup amd64 2:1.6.6-5ubuntu2.1 [123 kB]
Get:139 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 dnsmasq-base amd64 2.75-1ubuntu0.16.04.4 [295 kB]
Get:140 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 dpkg-dev all 1.18.4ubuntu1.4 [584 kB]
Get:141 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdpkg-perl all 1.18.4ubuntu1.4 [195 kB]
Get:142 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox amd64 59.0.1+build1-0ubuntu0.16.04.1 [44.5 MB]
Get:143 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 firefox-locale-en amd64 59.0.1+build1-0ubuntu0.16.04.1 [701 kB]
Get:144 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libdfu1 amd64 0.8.3-0ubuntu2 [48.7 kB]
Get:145 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 fwupdate-signed amd64 1.11.3+0.5-2ubuntu7 [28.1 kB]
Get:146 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 fwupdate amd64 0.5-2ubuntu7 [34.3 kB]
Get:147 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libfwup0 amd64 0.5-2ubuntu7 [13.4 kB]
Get:148 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libfwupd1 amd64 0.8.3-0ubuntu2 [33.1 kB]
Get:149 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 fwupd amd64 0.8.3-0ubuntu2 [120 kB]
Get:150 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpackagekit-glib2-16 amd64 0.8.17-4ubuntu6~gcc5.4ubuntu1.2 [101 kB]
Get:151 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gir1.2-packagekitglib-1.0 amd64 0.8.17-4ubuntu6~gcc5.4ubuntu1.2 [26.7 kB]
Get:152 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gir1.2-unity-5.0 amd64 7.1.4+16.04.20180209.1-0ubuntu1 [20.2 kB]
Get:153 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-accessibility-themes all 3.18.0-2ubuntu2 [2,298 kB]
Get:154 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-disk-utility amd64 3.18.3.1-1ubuntu1.1 [198 kB]
Get:155 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-software amd64 3.20.5-0ubuntu0.16.04.8 [11.7 kB]
Get:156 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-software amd64 3.20.5-0ubuntu0.16.04.8 [240 kB]
Get:157 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gnome-software-common all 3.20.5-0ubuntu0.16.04.8 [2,520 kB]
Get:158 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsnapd-glib1 amd64 1.13-0ubuntu0.16.04.1 [52.0 kB]
Get:159 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgtk2.0-common all 2.24.30-1ubuntu1.16.04.2 [123 kB]
Get:160 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgtk2.0-bin amd64 2.24.30-1ubuntu1.16.04.2 [9,834 B]
Get:161 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgail-common amd64 2.24.30-1ubuntu1.16.04.2 [112 kB]
Get:162 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgail18 amd64 2.24.30-1ubuntu1.16.04.2 [14.2 kB]
Get:163 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 gtk2-engines-pixbuf amd64 2.24.30-1ubuntu1.16.04.2 [19.0 kB]
Get:164 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgtk2.0-0 amd64 2.24.30-1ubuntu1.16.04.2 [1,775 kB]
Get:165 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gvfs-bin amd64 1.28.2-1ubuntu1~16.04.2 [55.2 kB]
Get:166 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gvfs-backends amd64 1.28.2-1ubuntu1~16.04.2 [300 kB]
Get:167 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gvfs-fuse amd64 1.28.2-1ubuntu1~16.04.2 [14.2 kB]
Get:168 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gvfs amd64 1.28.2-1ubuntu1~16.04.2 [91.5 kB]
Get:169 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gvfs-daemons amd64 1.28.2-1ubuntu1~16.04.2 [112 kB]
Get:170 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gvfs-libs amd64 1.28.2-1ubuntu1~16.04.2 [110 kB]
Get:171 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 gvfs-common all 1.28.2-1ubuntu1~16.04.2 [45.6 kB]
Get:172 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libepoxy0 amd64 1.3.1-1ubuntu0.16.04.2 [177 kB]
Get:173 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgweather-common all 3.18.2-0ubuntu0.2 [158 kB]
Get:174 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgweather-3-6 amd64 3.18.2-0ubuntu0.2 [63.4 kB]
Get:175 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libinput-bin amd64 1.6.3-1ubuntu1~16.04.1 [9,040 B]
Get:176 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libinput10 amd64 1.6.3-1ubuntu1~16.04.1 [74.0 kB]
Get:177 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libmbim-proxy amd64 1.14.0-1ubuntu0.16.04.1 [5,458 B]
Get:178 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libmbim-glib4 amd64 1.14.0-1ubuntu0.16.04.1 [65.6 kB]
Get:179 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libmm-glib0 amd64 1.6.4-1ubuntu0.16.04.1 [163 kB]
Get:180 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnautilus-extension1a amd64 1:3.18.4.is.3.14.3-0ubuntu6 [53.7 kB]
Get:181 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-glib-vpn1 amd64 1.2.6-0ubuntu0.16.04.2 [14.2 kB]
Get:182 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm0 amd64 1.2.6-0ubuntu0.16.04.2 [352 kB]
Get:183 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqmi-glib5 amd64 1.16.2-1ubuntu0.16.04.1 [360 kB]
Get:184 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqmi-proxy amd64 1.16.2-1ubuntu0.16.04.1 [5,486 B]
Get:185 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 modemmanager amd64 1.6.4-1ubuntu0.16.04.1 [604 kB]
Get:186 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 network-manager amd64 1.2.6-0ubuntu0.16.04.2 [1,972 kB]
Get:187 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 network-manager-gnome amd64 1.2.6-0ubuntu0.16.04.4 [291 kB]
Get:188 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnma0 amd64 1.2.6-0ubuntu0.16.04.4 [66.5 kB]
Get:189 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnma-common all 1.2.6-0ubuntu0.16.04.4 [5,684 B]
Get:190 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5core5a amd64 5.5.1+dfsg-16ubuntu7.5 [1,817 kB]
Get:191 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5dbus5 amd64 5.5.1+dfsg-16ubuntu7.5 [175 kB]
Get:192 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5network5 amd64 5.5.1+dfsg-16ubuntu7.5 [540 kB]
Get:193 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5gui5 amd64 5.5.1+dfsg-16ubuntu7.5 [2,290 kB]
Get:194 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5widgets5 amd64 5.5.1+dfsg-16ubuntu7.5 [2,252 kB]
Get:195 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5opengl5 amd64 5.5.1+dfsg-16ubuntu7.5 [128 kB]
Get:196 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5printsupport5 amd64 5.5.1+dfsg-16ubuntu7.5 [174 kB]
Get:197 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5sql5 amd64 5.5.1+dfsg-16ubuntu7.5 [104 kB]
Get:198 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5sql5-sqlite amd64 5.5.1+dfsg-16ubuntu7.5 [33.0 kB]
Get:199 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5test5 amd64 5.5.1+dfsg-16ubuntu7.5 [84.5 kB]
Get:200 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libqt5xml5 amd64 5.5.1+dfsg-16ubuntu7.5 [91.8 kB]
Get:201 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsnmp-base all 5.7.3+dfsg-1ubuntu4.1 [224 kB]
Get:202 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libsnmp30 amd64 5.7.3+dfsg-1ubuntu4.1 [811 kB]
Get:203 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 libva1 amd64 1.7.0-1ubuntu0.1 [45.4 kB]
Get:204 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libwacom-bin amd64 0.22-1~ubuntu16.04.1 [4,642 B]
Get:205 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libxatracker2 amd64 17.2.8-0ubuntu0~16.04.1 [1,102 kB]
Get:206 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-mono all 14.04+16.04.20171116-0ubuntu1 [177 kB]
Get:207 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 light-themes all 14.04+16.04.20171116-0ubuntu1 [153 kB]
Get:208 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-firmware all 1.157.17 [45.5 MB]
Get:209 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 mesa-vdpau-drivers amd64 17.2.8-0ubuntu0~16.04.1 [1,719 kB]
Get:210 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 nautilus-data all 1:3.18.4.is.3.14.3-0ubuntu6 [48.1 kB]
Get:211 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 session-shortcuts all 1.2ubuntu0.16.04.1 [2,624 B]
Get:212 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 snapd-login-service amd64 1.13-0ubuntu0.16.04.1 [11.6 kB]
Get:213 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-mobile-icons all 14.04+16.04.20171116-0ubuntu1 [6,841 kB]
Get:214 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 suru-icon-theme all 14.04+16.04.20171116-0ubuntu1 [1,626 kB]
Get:215 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-artwork all 1:14.04+16.04.20171116-0ubuntu1 [7,624 B]
Get:216 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 ubuntu-desktop amd64 1.361.1 [3,626 B]
Get:217 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unattended-upgrades all 0.90ubuntu0.9 [32.3 kB]
Get:218 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity-control-center-faces all 15.04.0+16.04.20171130-0ubuntu1 [180 kB]
Get:219 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 unity-scopes-runner all 7.1.4+16.04.20180209.1-0ubuntu1 [4,180 B]
Get:220 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 va-driver-all amd64 1.7.0-1ubuntu0.1 [4,534 B]
Get:221 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 xfonts-utils amd64 1:7.7+3ubuntu0.16.04.2 [74.6 kB]
Get:222 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 apparmor-profiles all 2.10.95-0ubuntu2.9 [31.1 kB]
Fetched 358 MB in 2min 27s (2,435 kB/s)                                        
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib4_1.2.6-0ubuntu0.16.04.2_amd64.deb  Connection timed out [IP: 2001:67c:1562::16 80]

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 
```

---

### Post by cariboo on 2018-03-17
I'd suggest you do what it says at the bottom of the output you posted:

```
sudo apt update && sudo apt -f install
```

then run

```
sudo apt autoremove
```

to get rid of all the unused kernels.

---

### Post by oldos2er on 2018-03-18
You can fix the NO_PUBKEY warning by installing the gpg key. ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1F3045A5DF7587C3
```

---

### Post by mollie4168 on 2018-03-20
Many thanks to you both!

---

