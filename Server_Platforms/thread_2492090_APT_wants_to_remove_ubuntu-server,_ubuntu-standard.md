---
title: "APT wants to remove ubuntu-server, ubuntu-standard &amp; ubuntu-minimal metapackages"
date: 2023-10-30
forum: Server Platforms
---

### Post by tanguypelado on 2023-10-30
Hey all,

Upon the routine apt update & apt dist-upgrade (which apparently I should replace with full-upgrade, but same behaviour) on two of my ubuntu 20.04 servers, I've discovered that APT wants to remove those packets : 

```
[FONT=monospace]
[/FONT][FONT=monospace][COLOR=#000000]cloud-init cloud-initramfs-copymods cloud-initramfs-dyn-netconf cryptsetup-initramfs [/COLOR]
  dbus-user-session dconf-gsettings-backend dconf-service friendly-recovery glib-networking 
  gsettings-desktop-schemas initramfs-tools initramfs-tools-core kpartx libappstream4 libnss-systemd 
  libpam-systemd libsoup2.4-1 mdadm modemmanager multipath-tools netplan.io open-iscsi overlayroot 
  packagekit packagekit-tools plymouth plymouth-theme-ubuntu-text policykit-1 sg3-utils-udev snapd 
  software-properties-common ubuntu-minimal ubuntu-server ubuntu-standard udev udisks2 upower
[/FONT]
[FONT=monospace] 
[/FONT]
```

Now I'm not in any way an ubuntu expert, but at least some of those packages seem useful to me (netplan, initramfs-tools, udev...) I'd understand the removal if there were some new packages installed in their place, but this isn't the case here. Am I missing something? Why would the metapackages be flagged for removal?

Useful (ish) stuff : 

lsb_release
```


[FONT=monospace][COLOR=#000000]DISTRIB_ID=Ubuntu [/COLOR]
DISTRIB_RELEASE=20.04 
DISTRIB_CODENAME=focal 
DISTRIB_DESCRIPTION="Ubuntu 20.04.6 LTS"

[/FONT]
```

apt source list : 
```


[FONT=monospace][COLOR=#000000]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to [/COLOR]
# newer versions of the distribution. 
deb http://archive.ubuntu.com/ubuntu focal main restricted 
# deb-src http://archive.ubuntu.com/ubuntu focal main restricted 

## Major bug fix updates produced after the final release of the 
## distribution. 
deb http://archive.ubuntu.com/ubuntu focal-updates main restricted 
# deb-src http://archive.ubuntu.com/ubuntu focal-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team. Also, please note that software in universe WILL NOT receive any 
## review or updates from the Ubuntu security team. 
deb http://archive.ubuntu.com/ubuntu focal universe 
# deb-src http://archive.ubuntu.com/ubuntu focal universe 
deb http://archive.ubuntu.com/ubuntu focal-updates universe 
# deb-src http://archive.ubuntu.com/ubuntu focal-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
deb http://archive.ubuntu.com/ubuntu focal multiverse 
# deb-src http://archive.ubuntu.com/ubuntu focal multiverse 
deb http://archive.ubuntu.com/ubuntu focal-updates multiverse 
# deb-src http://archive.ubuntu.com/ubuntu focal-updates multiverse 

## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
deb http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse 
# deb-src http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's 
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the 
## respective vendors as a service to Ubuntu users. 
# deb http://archive.canonical.com/ubuntu focal partner 
# deb-src http://archive.canonical.com/ubuntu focal partner 

deb http://archive.ubuntu.com/ubuntu focal-security main restricted 
# deb-src http://archive.ubuntu.com/ubuntu focal-security main restricted 
deb http://archive.ubuntu.com/ubuntu focal-security universe 
# deb-src http://archive.ubuntu.com/ubuntu focal-security universe 
deb http://archive.ubuntu.com/ubuntu focal-security multiverse 
# deb-src http://archive.ubuntu.com/ubuntu focal-security multiverse


[/FONT]
```

Cheers

---

### Post by ian-weisser on 2023-10-30
Show us complete input and output.
That means the full apt command you used, and then the entire output.
The edited summary so far does not contain enough information.

---

### Post by tanguypelado on 2023-10-30
Here's the full output from apt full-upgrade (this is a french system, hence the locale)

```
[FONT=monospace][COLOR=#54FF54][/COLOR][/FONT][FONT=monospace][COLOR=#54FF54]**user@testbed1-up-nyx**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ LC_ALL=C sudo apt full-upgrade  [/COLOR]
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Calculating upgrade... Done 
The following packages were automatically installed and are no longer required: 
  busybox-initramfs cryptsetup cryptsetup-bin cryptsetup-run eatmydata finalrd 
  gir1.2-packagekitglib-1.0 glib-networking-common glib-networking-services initramfs-tools-bin 
  klibc-utils libatasmart4 libblockdev-crypto2 libblockdev-fs2 libblockdev-loop2 libblockdev-part-err2 
  libblockdev-part2 libblockdev-swap2 libblockdev-utils2 libblockdev2 libdconf1 libeatmydata1 
  libglib2.0-bin libgstreamer1.0-0 libimobiledevice6 libisns0 libklibc libnetplan0 libnspr4 libnss3 
  libpackagekit-glib2-18 libparted-fs-resize0 libplist3 libplymouth5 libpolkit-agent-1-0 libproxy1v5 
  libsgutils2-2 libstemmer0d libudisks2-0 liburcu6 libusbmuxd6 libvolume-key1 
  linux-headers-5.15.0-79-generic linux-headers-5.4.0-163 linux-headers-5.4.0-163-generic 
  linux-hwe-5.15-headers-5.15.0-79 linux-image-5.15.0-79-generic linux-image-5.4.0-163-generic 
  linux-modules-5.15.0-79-generic linux-modules-5.4.0-163-generic 
  linux-modules-extra-5.15.0-79-generic linux-modules-extra-5.4.0-163-generic lz4 
  python3-importlib-metadata python3-jinja2 python3-json-pointer python3-jsonpatch python3-jsonschema 
  python3-markupsafe python3-more-itertools python3-pyrsistent python3-software-properties 
  python3-zipp sg3-utils squashfs-tools unattended-upgrades usb-modeswitch usb-modeswitch-data usbmuxd 
Use 'sudo apt autoremove' to remove them. 
Get more security updates through Ubuntu Pro with 'esm-apps' enabled: 
  libwireshark13 libwsutil11 iperf3 libwiretap10 tshark wireshark-common 
  libiperf0 libwireshark-data 
Learn more about Ubuntu Pro at https://ubuntu.com/pro 
# 
# Canonical released microcode updates for both Intel (CVE-2022-40982) and AMD 
# (CVE-2023-20593). ‘Unattended upgrades’ provide security updates by default. 
# Ensure it remains enabled to always get all updates as they become available. 
# 
The following packages will be REMOVED: 
  cloud-init cloud-initramfs-copymods cloud-initramfs-dyn-netconf cryptsetup-initramfs 
  dbus-user-session dconf-gsettings-backend dconf-service friendly-recovery glib-networking 
  gsettings-desktop-schemas initramfs-tools initramfs-tools-core kpartx libappstream4 libnss-systemd 
  libpam-systemd libsoup2.4-1 mdadm modemmanager multipath-tools netplan.io open-iscsi overlayroot 
  packagekit packagekit-tools plymouth plymouth-theme-ubuntu-text policykit-1 sg3-utils-udev snapd 
  software-properties-common ubuntu-minimal ubuntu-server ubuntu-standard udev udisks2 upower 
The following packages have been kept back: 
  btrfs-progs libext2fs2 libsystemd0 
The following packages will be upgraded: 
  libudev1 
1 upgraded, 0 newly installed, 37 to remove and 3 not upgraded. 
Need to get 168 kB of archives. 
After this operation, 201 MB disk space will be freed. 
Do you want to continue? [Y/n] ^C 
[COLOR=#54FF54]**user@testbed1-up-nyx**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ [/COLOR]


[/FONT]

```

Best Regards

---

### Post by ian-weisser on 2023-10-30
There are typically two possibilities:

1. Something was recently removed that all those metapackages depend upon.
2. Something was recently installed that --directly or indirectly-- is incompatible with most of your system. Common with wrong-release packages and non-Ubuntu sources.

Review your apt log (/var/log/apt/history.log) to see what you have recently added or removed that might fit one of the criteria.

Also review the apt dependencies of ubuntu-minimal. It's likely to be a removal or replacement of one of those packages...or one of their dependencies.

The important damage is already done. You already installed (or removed) the offender. Now it's a matter of locating that offender.

---

### Post by tanguypelado on 2023-10-30
Alright, as usual, I am an idiot. 

I had the Proxmox Backup Client installed, but it was using the wrong source (bullseye instead of buster). This apparently causes APT to properly freak out (it didn't before, something dependency wise must have gone haywire, kind of expected when you mix and match OSses and versions). 

I apologize for the inconvenience. If anyone in the future finds this thread : 

- If you have similar issues to me
- you're using the Proxmox backup client

Check if you're using the correct version of the apt repos for your PBS client. 

Ian, I thank you for helping me. 


Cheers

---

### Post by MAFoElffen on 2023-10-30
One thing that might help with that is to run the UbuntuForums 'system-info' script on it from my signature line, and look at the User Manually Installed packages list and Snap packages near the end of the report.

I just spun up a 20.04.6 Server template from my test-suite, of a Server just after a fresh install, without any updates, yet... Ad ran the script on it. This is what it say for comparison:
```

   --- User Installed Package List:
base-files
base-passwd
bash
cloud-init
dash
diffutils
efibootmgr
findutils
grep
grub-efi-amd64
grub-efi-amd64-signed
gzip
hostname
init
libdebconfclient0
libfwupdplugin1
libsodium23
libxmlb1
linux-generic
ncurses-base
ncurses-bin
openssh-server
python3-nacl
python3-pymacaroons
shim-signed
sysvinit-utils
ubuntu-minimal
ubuntu-server
ubuntu-standard

   --- Installed Snap Package List:
core20
lxd
snapd

```

---

