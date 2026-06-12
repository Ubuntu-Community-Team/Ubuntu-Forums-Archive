---
title: "Plucky with my vpn again"
date: 2024-11-05
forum: Ubuntu Development Version
---

### Post by 1fallen on 2024-11-05
Not the usual expected result:
```
Installing:                     
  surfshark

Installing dependencies:
  amd64-microcode  libmozjs-128-0                      linux-modules-extra-6.11.0-1001-realtime
  gjs              libpkcs11-helper1t64                network-manager-openvpn
  intel-microcode  linux-image-6.11.0-1001-realtime    openvpn
  iucode-tool      linux-image-realtime
  libgjs0g         linux-modules-6.11.0-1001-realtime

Suggested packages:
  linux-doc                       linux-headers-6.11.0-1001-realtime  easy-rsa
  | linux-realtime-source-6.11.0  openvpn-dco-dkms
  linux-realtime-tools            openvpn-systemd-resolved

Summary:
  Upgrading: 0, Installing: 14, Removing: 0, Not Upgrading: 0
  Download size: 171 MB / 375 MB
  Space needed: 1,395 MB / 416 GB available
  &#9492;&#9472; in /boot:  95.0 MB / 1,792 MB available


```
I'll wait to file a bug. More research is needed first.
Current Kernel:
```
Kernel: 6.11.0-8-generic
```
EDIT: This is snap-less system:
```
sudo apt install snapd
Package snapd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Error: Package 'snapd' has no installation candidate

```

EDIT This kernel needs a ton of work, constant logouts just opening any Application....LOL
This one>>>"linux-image-6.11.0-1001-realtime " Best Avoid this one....:P
```
linux-headers-6.11.0-1001-realtime.0.crash
nvidia-kernel-source-555.0.crash
_opt_Surfshark_surfshark.1000.crash
_usr_bin_blueman-applet.1000.crash
_usr_bin_conky.1000.crash
_usr_bin_firewall-applet.1000.crash
_usr_bin_pipewire.1000.crash
_usr_bin_xfce4-panel.1000.crash
_usr_bin_xfsettingsd.1000.crash
_usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.crash
_usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.upload
_usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-2.0.1000.uploaded
_usr_lib_xorg_Xorg.0.crash

```

EDIT2 for removal of the un-wanted kernel:
```
apt -s autoremove linux-image-6.11.0-1001-realtime
NOTE: This is only a simulation!
      apt needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!

REMOVING:                       
  amd64-microcode  iucode-tool     libpkcs11-helper1t64              network-manager-openvpn
  gjs              libgjs0g        linux-image-6.11.0-1001-realtime  openvpn
  intel-microcode  libmozjs-128-0  linux-image-realtime              surfshark

Summary:
  Upgrading: 0, Installing: 0, Removing: 12, Not Upgrading: 0
Remv surfshark [3.1.0-4987]
Remv linux-image-realtime [6.11.0-1001.1]
Remv amd64-microcode [3.20240116.2+nmu1ubuntu1.1]
Remv gjs [1.82.0-2]
Remv intel-microcode [3.20240910.0ubuntu1]
Remv iucode-tool [2.3.1-3build1]
Remv libgjs0g [1.82.0-2]
Remv libmozjs-128-0 [128.3.0-1]
Remv network-manager-openvpn [1.12.0-1]
Remv openvpn [2.6.12-1ubuntu1]
Remv libpkcs11-helper1t64 [1.30.0-1]
Remv linux-image-6.11.0-1001-realtime [6.11.0-1001.1]

```
Surfshark lays this on Buntu.....](*,)

EDIT3: solved it myself, blew my whole /boot out and then reinstalled my choice, for now.
```
apt list --installed|grep linux-image

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-image-6.11.0-8-generic/plucky,now 6.11.0-8.8 amd64 [installed]
linux-image-generic-hwe-24.04-edge/plucky,now 6.11.0-8.8 amd64 [installed]

```
Leaving Open for now.

---

### Post by 1fallen on 2024-11-06
What I think (and I'm 99% sure) happened is, A jump from Noble to Plucky (not the right way to upgrade) It dropped some of the needed kernel modules so when I went to install Surfshark it would guess on what kernel it thought it needed ie:
```
apt depends surfshark
surfshark
  Depends: libnotify4
  Depends: libxtst6
  Depends: libnss3
  Depends: gjs
  Depends: network-manager (>= 1.20.0)
  Depends: network-manager-openvpn
  Depends: gir1.2-nm-1.0
 |Depends: <wireguard-dkms> (>= 0.0.20200121-2)
  Depends: <wireguard-modules> (>= 0.0.20191219)
    linux-image-aws
    linux-image-azure
    linux-image-azure-fde
    linux-image-gcp
    linux-image-generic
    linux-image-generic-hwe-24.04
    linux-image-generic-hwe-24.04-edge
    linux-image-lowlatency
    linux-image-oracle
    linux-image-realtime
    linux-image-virtual
    linux-image-virtual-hwe-24.04
    linux-image-virtual-hwe-24.04-edge
 |Depends: gnome-keyring
  Depends: kwalletmanager
  Depends: zip
    zip:i386
  Depends: curl
    curl:i386
  Depends: dbus
    dbus:i386
  Depends: iproute2
    iproute2:i386
  Depends: iptables
    iptables:i386
  Depends: grep
    grep:i386
  Depends: sed
    sed:i386
  Depends: lsb-base (>= 3.2-14)
    sysvinit-utils:i386
    sysvinit-utils
  Recommends: libappindicator3-1
    libayatana-appindicator3-1
  Recommends: policykit-1
    policykit-1:i386
 |Recommends: <polkit-1-auth-agent>
    gnome-flashback
    gnome-shell
    lxpolkit
    lxqt-policykit
    mate-polkit
    phosh
    policykit-1-gnome
    polkit-kde-agent-1
    ukui-polkit
 |Recommends: policykit-1-gnome
  Recommends: <polkit-kde-1>
  Recommends: fonts-noto-color-emoji
  Recommends: libsecret-1-0

```
I really had to do a lot of really bad removals to fix this kernel puzzle, but All Good now.

---

