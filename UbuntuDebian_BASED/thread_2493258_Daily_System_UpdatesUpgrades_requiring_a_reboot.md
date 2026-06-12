---
title: "Daily System Updates/Upgrades requiring a reboot"
date: 2023-12-08
forum: Ubuntu/Debian BASED
---

### Post by rusty.hinge on 2023-12-08
Something has changed.  My OS is Pop!_22.04 with KDE Plasma 5.24.7, but I'm seeing the same behavior on Ubuntu 22.04.  I stay pretty current with updates/ upgrades.  Lately I've been getting updates/upgrades daily that require a reboot.  This feel very Winders-esk.  Now I see we my be getting our own Blue Screen of Death.  Has Canonical been purchased by Microsoft?

---

### Post by howefield on 2023-12-08
Moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by ian-weisser on 2023-12-08
Show us each set upgrades that require rebooting. The list is time-stamped in your /var/log/apt/history.log.
Do not show us the entire log. Just the entries for each day that prompted you for a reboot.

---

### Post by rusty.hinge on 2023-12-09
I am not familiar with the command "packagekit"  I don't know if that triggers the reboot message or not.  The following is just November and December's entries.  
Thank you in advance. 
 
```
Start-Date: 2023-11-03  10:02:30
Commandline: packagekit role='update-packages'
Upgrade: libsndfile1:amd64 (1.0.31-2build1, 1.0.31-2ubuntu0.1)
End-Date: 2023-11-03  10:02:31

Start-Date: 2023-11-06  05:57:55
Commandline: packagekit role='update-packages'
Upgrade: libgssapi-krb5-2:amd64 (1.19.2-2ubuntu0.2, 1.19.2-2ubuntu0.3), libkrb5support0:amd64 (1.19.2-2ubuntu0.2, 1.19.2-2ubuntu0.3), libkrb5-3:amd64 (1.19.2-2ubuntu0.2, 1.19.2-2ubuntu0.3), libk5crypto3:amd64 (1.19.2-2ubuntu0.2, 1.19.2-2ubuntu0.3)
End-Date: 2023-11-06  05:57:56

Start-Date: 2023-11-07  13:15:40
Commandline: packagekit role='update-packages'
Upgrade: python3-urllib3:amd64 (1.26.5-1~exp1, 1.26.5-1~exp1ubuntu0.1)
End-Date: 2023-11-07  13:15:40

Start-Date: 2023-11-09  07:49:27
Commandline: packagekit role='update-packages'
Upgrade: pop-launcher:amd64 (1.2.2~1691078703~22.04~0febac5, 1.2.2~1699376420~22.04~b1f6002), firefox:amd64 (1:118.0.2~1696960505~22.04~f0ebfae, 1:119.0~1698447952~22.04~60cc67a), system76-driver:amd64 (20.04.81~1695239320~22.04~ec593da, 20.04.82~1699289493~22.04~dfbce5b), teamviewer:amd64 (15.48.1, 15.48.3)
End-Date: 2023-11-09  07:49:33

Start-Date: 2023-11-13  06:52:59
Commandline: packagekit role='update-packages'
Upgrade: firmware-sof-signed:amd64 (2.0-1ubuntu4.1, 2.0-1ubuntu4.2)
End-Date: 2023-11-13  06:52:59

Start-Date: 2023-11-14  06:57:54
Commandline: packagekit role='update-packages'
Upgrade: system76-firmware-daemon:amd64 (1.0.54~1698255341~22.04~75cb1f6, 1.0.55~1699483593~22.04~cb768e7), python3-repolib:amd64 (2.2.1~1694470620~22.04~4acc78e, 2.2.1~1699647578~22.04~43c8b87), firefox:amd64 (1:119.0~1698447952~22.04~60cc67a, 1:119.0.1~1699475695~22.04~e5844ba), libprocps8:amd64 (2:3.3.17-6ubuntu2, 2:3.3.17-6ubuntu2.1), procps:amd64 (2:3.3.17-6ubuntu2, 2:3.3.17-6ubuntu2.1)
End-Date: 2023-11-14  06:57:57

Start-Date: 2023-11-15  07:32:22
Commandline: packagekit role='update-packages'
Upgrade: apt:amd64 (2.4.10, 2.4.11), libapt-pkg6.0:amd64 (2.4.10, 2.4.11), apt-utils:amd64 (2.4.10, 2.4.11)
End-Date: 2023-11-15  07:32:23

Start-Date: 2023-11-16  07:02:54
Commandline: packagekit role='update-packages'
Upgrade: libglx-mesa0:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), libpipewire-0.3-common:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), pipewire-pulse:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), libgbm1:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), pipewire:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), libxatracker2:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), mesa-va-drivers:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), libgl1-mesa-dri:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), libspa-0.2-jack:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), libspa-0.2-bluetooth:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), pipewire-jack:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), gstreamer1.0-pipewire:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), mesa-vulkan-drivers:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), pipewire-avb:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), pipewire-bin:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), libglapi-mesa:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), libspa-0.2-modules:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), teamviewer:amd64 (15.48.3, 15.48.4), libegl-mesa0:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), libpipewire-0.3-modules:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), mesa-vdpau-drivers:amd64 (23.1.3-1pop0~1689084530~22.04~0618746, 23.2.1-1pop0~1699535617~22.04~6cd9a72), intel-microcode:amd64 (3.20230808.0ubuntu0.22.04.1, 3.20231114.0ubuntu0.22.04.1), pipewire-alsa:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), libpipewire-0.3-0:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde), libspa-0.2-avb:amd64 (0.3.82~1697398205~22.04~5887ccb, 0.3.84~1699895474~22.04~f909dde)
End-Date: 2023-11-16  07:03:12

Start-Date: 2023-11-17  06:31:43
Commandline: packagekit role='update-packages'
Install: ubuntu-pro-client-l10n:amd64 (30~22.04, automatic)
Upgrade: ubuntu-advantage-tools:amd64 (29.4~22.04, 30~22.04)
End-Date: 2023-11-17  06:31:49

Start-Date: 2023-11-21  11:13:09
Commandline: packagekit role='update-packages'
Upgrade: avahi-autoipd:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2), avahi-utils:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2), libnode72:amd64 (12.22.9~dfsg-1ubuntu3.1, 12.22.9~dfsg-1ubuntu3.2), libavahi-common-data:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2), libavahi-core7:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2), gir1.2-javascriptcoregtk-4.0:amd64 (2.42.1-0ubuntu0.22.04.1, 2.42.2-0ubuntu0.22.04.1), gir1.2-webkit2-4.0:amd64 (2.42.1-0ubuntu0.22.04.1, 2.42.2-0ubuntu0.22.04.1), avahi-daemon:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2), nodejs:amd64 (12.22.9~dfsg-1ubuntu3.1, 12.22.9~dfsg-1ubuntu3.2), libjavascriptcoregtk-4.0-18:amd64 (2.42.1-0ubuntu0.22.04.1, 2.42.2-0ubuntu0.22.04.1), libavahi-common3:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2), libavahi-glib1:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2), nodejs-doc:amd64 (12.22.9~dfsg-1ubuntu3.1, 12.22.9~dfsg-1ubuntu3.2), libwebkit2gtk-4.0-37:amd64 (2.42.1-0ubuntu0.22.04.1, 2.42.2-0ubuntu0.22.04.1), libgnutls30:amd64 (3.7.3-4ubuntu1.2, 3.7.3-4ubuntu1.3), libavahi-client3:amd64 (0.8-5ubuntu5.1, 0.8-5ubuntu5.2)
End-Date: 2023-11-21  11:13:12

Start-Date: 2023-11-22  06:14:41
Commandline: packagekit role='update-packages'
Upgrade: evince:amd64 (42.3-0ubuntu3, 42.3-0ubuntu3.1), software-properties-qt:amd64 (0.99.22.7, 0.99.22.8), apparmor:amd64 (3.0.4-2ubuntu2.2, 3.0.4-2ubuntu2.3), software-properties-common:amd64 (0.99.22.7, 0.99.22.8), libevdocument3-4:amd64 (42.3-0ubuntu3, 42.3-0ubuntu3.1), libapparmor1:amd64 (3.0.4-2ubuntu2.2, 3.0.4-2ubuntu2.3), python3-software-properties:amd64 (0.99.22.7, 0.99.22.8), libevview3-3:amd64 (42.3-0ubuntu3, 42.3-0ubuntu3.1), evince-common:amd64 (42.3-0ubuntu3, 42.3-0ubuntu3.1)
End-Date: 2023-11-22  06:14:47

Start-Date: 2023-11-24  17:37:46
Commandline: packagekit role='update-packages'
Upgrade: libpoppler-qt5-1:amd64 (22.02.0-2ubuntu0.2, 22.02.0-2ubuntu0.3), libnghttp2-14:amd64 (1.43.0-1build3, 1.43.0-1ubuntu0.1), libtiff5:amd64 (4.3.0-6ubuntu0.6, 4.3.0-6ubuntu0.7), tracker-miner-fs:amd64 (3.3.0-1, 3.3.3-0ubuntu0.20.04.1), libpoppler-cpp0v5:amd64 (22.02.0-2ubuntu0.2, 22.02.0-2ubuntu0.3), poppler-utils:amd64 (22.02.0-2ubuntu0.2, 22.02.0-2ubuntu0.3), libpoppler-glib8:amd64 (22.02.0-2ubuntu0.2, 22.02.0-2ubuntu0.3), libpoppler118:amd64 (22.02.0-2ubuntu0.2, 22.02.0-2ubuntu0.3), tracker-extract:amd64 (3.3.0-1, 3.3.3-0ubuntu0.20.04.1)
End-Date: 2023-11-24  17:37:47

Start-Date: 2023-11-29  17:37:59
Commandline: packagekit role='update-packages'
Upgrade: libperl5.34:amd64 (5.34.0-3ubuntu1.2, 5.34.0-3ubuntu1.3), openjdk-11-jdk:amd64 (11.0.20.1+1-0ubuntu1~22.04, 11.0.21+9-0ubuntu1~22.04), openjdk-11-jre:amd64 (11.0.20.1+1-0ubuntu1~22.04, 11.0.21+9-0ubuntu1~22.04), openjdk-11-jre-headless:amd64 (11.0.20.1+1-0ubuntu1~22.04, 11.0.21+9-0ubuntu1~22.04), system76-firmware-daemon:amd64 (1.0.55~1699483593~22.04~cb768e7, 1.0.56~1701196208~22.04~f0fef37), python3.10:amd64 (3.10.12-1~22.04.2, 3.10.12-1~22.04.3), libfirmware-manager:amd64 (0.1.2~1698259923~22.04~f3ead34, 0.1.2~1700606232~22.04~c2c7aac), openjdk-11-jdk-headless:amd64 (11.0.20.1+1-0ubuntu1~22.04, 11.0.21+9-0ubuntu1~22.04), gnome-control-center-faces:amd64 (1:41.4-1ubuntu12pop1~1682958295~22.04~2c30e97, 1:41.4-1ubuntu12pop1~1701107237~22.04~eba04d3), perl:amd64 (5.34.0-3ubuntu1.2, 5.34.0-3ubuntu1.3), libpython3.10-minimal:amd64 (3.10.12-1~22.04.2, 3.10.12-1~22.04.3), firmware-sof-signed:amd64 (2.0-1ubuntu4.2, 2.0-1ubuntu4.4), libpython3.10-stdlib:amd64 (3.10.12-1~22.04.2, 3.10.12-1~22.04.3), firmware-manager-shared:amd64 (0.1.2~1698259923~22.04~f3ead34, 0.1.2~1700606232~22.04~c2c7aac), firefox:amd64 (1:119.0.1~1699475695~22.04~e5844ba, 1:120.0~1701107967~22.04~53ee2d6), ifupdown:amd64 (0.8.36+nmu1ubuntu3, 0.8.36+nmu1ubuntu3.1), libpython3.10:amd64 (3.10.12-1~22.04.2, 3.10.12-1~22.04.3), libgstreamer-plugins-bad1.0-0:amd64 (1.20.3-0ubuntu1, 1.20.3-0ubuntu1.1), libfreerdp2-2:amd64 (2.6.1+dfsg1-3ubuntu2.4, 2.6.1+dfsg1-3ubuntu2.5), gnome-control-center-data:amd64 (1:41.4-1ubuntu12pop1~1682958295~22.04~2c30e97, 1:41.4-1ubuntu12pop1~1701107237~22.04~eba04d3), linux-firmware:amd64 (20230815.git0e048b06-0ubuntu1+system76~1692716226~22.04~7d1b0aa, 20230919.git3672ccab-0ubuntu2.4+system76~1700581757~22.04~3901c42), libwinpr2-2:amd64 (2.6.1+dfsg1-3ubuntu2.4, 2.6.1+dfsg1-3ubuntu2.5), libfreerdp-server2-2:amd64 (2.6.1+dfsg1-3ubuntu2.4, 2.6.1+dfsg1-3ubuntu2.5), system76-driver:amd64 (20.04.82~1699289493~22.04~dfbce5b, 20.04.83~1701196506~22.04~be90e3f), firmware-manager-notify:amd64 (0.1.2~1698259923~22.04~f3ead34, 0.1.2~1700606232~22.04~c2c7aac), perl-base:amd64 (5.34.0-3ubuntu1.2, 5.34.0-3ubuntu1.3), gnome-control-center:amd64 (1:41.4-1ubuntu12pop1~1682958295~22.04~2c30e97, 1:41.4-1ubuntu12pop1~1701107237~22.04~eba04d3), libfreerdp-client2-2:amd64 (2.6.1+dfsg1-3ubuntu2.4, 2.6.1+dfsg1-3ubuntu2.5), python3.10-minimal:amd64 (3.10.12-1~22.04.2, 3.10.12-1~22.04.3), perl-modules-5.34:amd64 (5.34.0-3ubuntu1.2, 5.34.0-3ubuntu1.3)
End-Date: 2023-11-29  17:38:18

Start-Date: 2023-12-01  06:59:52
Commandline: packagekit role='update-packages'
Upgrade: openvpn:amd64 (2.5.5-1ubuntu3.1, 2.5.9-0ubuntu0.22.04.2)
End-Date: 2023-12-01  06:59:53

Start-Date: 2023-12-08  10:05:22
Commandline: packagekit role='update-packages'
Install: liblua5.4-0:amd64 (5.4.4-1, automatic)
Upgrade: libcurl4:amd64 (7.81.0-1ubuntu1.14, 7.81.0-1ubuntu1.15), libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.14, 7.81.0-1ubuntu1.15), libfirmware-manager:amd64 (0.1.2~1700606232~22.04~c2c7aac, 0.1.2~1701473591~22.04~fc93648), libpipewire-0.3-common:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), pipewire-pulse:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), libpop-desktop-widget:amd64 (0.2.0~1695656117~22.04~10ded1d, 0.2.0~1701473531~22.04~8a5ca3c), firmware-manager-shared:amd64 (0.1.2~1700606232~22.04~c2c7aac, 0.1.2~1701473591~22.04~fc93648), pipewire:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), firefox:amd64 (1:120.0~1701107967~22.04~53ee2d6, 1:120.0.1~1701380578~22.04~14fee3e), libc6:amd64 (2.35-0ubuntu3.4, 2.35-0ubuntu3.5), locales:amd64 (2.35-0ubuntu3.4, 2.35-0ubuntu3.5), libspa-0.2-jack:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), libspa-0.2-bluetooth:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), pipewire-jack:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), gstreamer1.0-pipewire:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), pipewire-avb:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), pipewire-bin:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), pop-shell:amd64 (1.1.0~1698186494~22.04~3386f42, 1.1.0~1701464844~22.04~64cfa5d), libc-dev-bin:amd64 (2.35-0ubuntu3.4, 2.35-0ubuntu3.5), firmware-manager-notify:amd64 (0.1.2~1700606232~22.04~c2c7aac, 0.1.2~1701473591~22.04~fc93648), libspa-0.2-modules:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), libc-bin:amd64 (2.35-0ubuntu3.4, 2.35-0ubuntu3.5), libc-devtools:amd64 (2.35-0ubuntu3.4, 2.35-0ubuntu3.5), libc6-dbg:amd64 (2.35-0ubuntu3.4, 2.35-0ubuntu3.5), libc6-dev:amd64 (2.35-0ubuntu3.4, 2.35-0ubuntu3.5), curl:amd64 (7.81.0-1ubuntu1.14, 7.81.0-1ubuntu1.15), libpipewire-0.3-modules:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), python3-cryptography:amd64 (3.4.8-1ubuntu2, 3.4.8-1ubuntu2.1), wireplumber:amd64 (0.4.14-1pop1~1682008167~22.04~dee6d71, 0.4.16~1700669479~22.04~7cc8205), pipewire-alsa:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), libwireplumber-0.4-0:amd64 (0.4.14-1pop1~1682008167~22.04~dee6d71, 0.4.16~1700669479~22.04~7cc8205), libpipewire-0.3-0:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5), libspa-0.2-avb:amd64 (0.3.84~1699895474~22.04~f909dde, 1.0.0~1701092078~22.04~594e8f5)
End-Date: 2023-12-08  10:06:26
```

---

### Post by ian-weisser on 2023-12-09
> **ian-weisser said:**
> Do not show us the entire log. Just the entries for each day that prompted you for a reboot.

Since you decided to show us the entire log anyway, now you need to tell us which days resulted in a prompt for reboot.

---

### Post by rusty.hinge on 2023-12-09
I apologize,  to the best of my knowledge all of them.  The fact that there were so many "System Upgrade" requiring reboot so often is what got my dander up.  
Start-Date: 2023-11-03  10:02:30
Start-Date: 2023-11-06  05:57:55
Start-Date: 2023-11-07  13:15:40
Start-Date: 2023-11-09  07:49:27
Start-Date: 2023-11-13  06:52:59
Start-Date: 2023-11-15  07:32:22
Start-Date: 2023-11-16  07:02:54
Start-Date: 2023-11-17  06:31:43
Start-Date: 2023-11-21  11:13:09
Start-Date: 2023-11-22  06:14:41
Start-Date: 2023-11-24  17:37:46
Start-Date: 2023-11-29  17:37:59
Start-Date: 2023-12-01  06:59:52
Start-Date: 2023-12-08  10:05:22

---

### Post by rusty.hinge on 2023-12-09
Just in

Start-Date: 2023-12-09  10:10:06
Commandline: packagekit role='update-packages'
Upgrade: system76-scheduler:amd64 (2.0.0~1683907952~22.04~5c20d3d, 2.0.0~1701988455~22.04~b8d6545), wireplumber:amd64 (0.4.16~1700669479~22.04~7cc8205, 0.4.17~1701792620~22.04~e8b4d60), libwireplumber-0.4-0:amd64 (0.4.16~1700669479~22.04~7cc8205, 0.4.17~1701792620~22.04~e8b4d60)
End-Date: 2023-12-09  10:10:07

---

### Post by #&amp;thj^% on 2023-12-09
You can narrow thing down, and find why with:
```
sudo cat /var/run/reboot-required

```
another tool is: (needsrestart) you may have to install it.
```
needrestart
Scanning processes...    
```

---

### Post by rusty.hinge on 2023-12-09
ted@myLio:~$ sudo cat /var/run/reboot-required
cat: /var/run/reboot-required: No such file or directory

ted@myLio:~$ needrestart
Scanning processes...                                                                                                        
ted@myLio:~$

---

### Post by #&amp;thj^% on 2023-12-09
If anything needed it, it would show as:
```
 needrestart
Scanning processes...                                                                    
Your outdated processes:
applet.py[3320], dbus-daemon[2650, 3049], firewall-applet[3373], gvfs-gphoto2-vo[3539],
 panel-9-pulseau[3166], systemd[2598], Thunar[3132], update-notifier[3350],
 xfce4-power-man[3317], xfdesktop[3144], xfsettingsd[3108]

``` 
Normally if the file
```

/var/run/reboot-required 

```
exists you should reboot.

---

### Post by rusty.hinge on 2023-12-11
I thought that maybe the "/var/run/reboot-required" file was removed upon rebooting.  because I never found it.  But this evening I received System Updates and requesting a reboot to install.   There still is no "reboot-required file. 

Start-Date: 2023-12-09  10:41:18
Commandline: apt install needrestart
Requested-By: ted (1000)
Install: libintl-perl:amd64 (1.26-3build2, automatic), libsort-naturally-perl:amd64 (1.03-2, automatic), libmodule-find-perl:amd64 (0.15-1, automatic), libterm-readkey-perl:amd64 (2.38-1build4, automatic), needrestart:amd64 (3.5-5ubuntu2.1), libintl-xs-perl:amd64 (1.26-3build2, automatic), libproc-processtable-perl:amd64 (0.634-1build1, automatic), libmodule-scandeps-perl:amd64 (1.31-1, automatic)
End-Date: 2023-12-09  10:41:19

---

### Post by ajgreeny on 2023-12-11
As far as I'm aware not all Debian based distros create that /var/run/reboot required file; certainly my Debian-sid install never does so I wonder if this is a situation where PopOS also does not make use of that method.

---

### Post by ian-weisser on 2023-12-11
> **rusty.hinge said:**
>  [...] But this evening I received System Updates and requesting a reboot to install. [...] 

Start-Date: 2023-12-09  10:41:18
Commandline: apt install needrestart
Requested-By: ted (1000)
Install: libintl-perl:amd64 (1.26-3build2, automatic), libsort-naturally-perl:amd64 (1.03-2, automatic), libmodule-find-perl:amd64 (0.15-1, automatic), libterm-readkey-perl:amd64 (2.38-1build4, automatic), needrestart:amd64 (3.5-5ubuntu2.1), libintl-xs-perl:amd64 (1.26-3build2, automatic), libproc-processtable-perl:amd64 (0.634-1build1, automatic), libmodule-scandeps-perl:amd64 (1.31-1, automatic)
End-Date: 2023-12-09  10:41:19

That is not System Updates.
That is you installing needrestart.
See the Commandline: field.

---

### Post by TheFu on 2023-12-11
I test each system, after patching, for the existence of /var/run/reboot-required.
If that file doesn't exist, I don't reboot.  Been doing this for decades, including 22.04 release (ubuntu and Mint).  If something changed after that, it is news to me.

It works on some Debian releases too ... or I'd never reboot my email gateway servers either.

As for needing to reboot all the time, I have this to say.
Do you patch more than once a week?  Why?  If a bad patch comes through and you are patching multiple times a day, your system might see 3 different versions and claim a reboot is needed 3 times.  I've been patching weekly (usually Sat mornings), so at most, I'll reboot once a week, if that.  Often, I'll patch on Saturday, but not reboot, if a reboot is needed, until Sunday.
```
$ uptime
 06:37:45 up 2 days, 22:00,  5 users,  
```
For a desktop, I can't imagine why people would patch more than once a week.
For a server, it is important to watch the bug reports for critical fixes that relate to your specific software.  My servers run all sorts of public services and sometimes those have critical issues that actually impact security.  That hardly ever actually happens. Sure, there are critical issues, but the specific nature of the problem isn't something my server(s) use, so it can wait.  

In the last 15 yrs, I've needed to patch mid-week less than 5 times and only 1 of the servers was impacted by those critical fixes.  Part of that mitigation is that I don't run php webapps on the public internet and we don't use wordpress or drupal or other often-hacked CMS.  

Additionally, our security is setup in layers to prevent bad inputs from ever getting to our webapps.  So, if there is a bug in a webapp we use, it is likely some special POST/GET request is needed to begin the attack, often through an administration page.  Those are blocked from access upstream before they ever hit the webapp server.  This makes sleeping pretty easy.  

We have automated, daily, versioned, backups that contain at least 90 days if not 365 days of versioned backups stored on a system that isn't able to reach over the internet.  The at-risk servers don't "push" their backups, rather, the backup server "pulls" the backups from each client system.  The client systems don't have any way to contact the backup server and certainly cannot access the backup storage directly.  The restore of backups has to be "pushed" to the clients as well. It is a subtle thing, but drastically changes security risks.

With versioned backups, we can look through the versions and find where any attacks started. That's happened a few times over the decades and been really helpful.  Finding the smoking attack 13 days before we noticed it, meant we could check all the other systems on the LAN for issues around the same time as the base starting point. Without versioned backups, we'd have to just blow away every system and start over to ensure some root kit wasn't left behind.

Security isn't just "patching", there is network architecture, systems architecture, storage architecture, backup and recovery design all to mitigate what can be done by nefarious actors. Patching is important, but not the only thing.  Security always has layers.   When possible, we'll use read-only mounts for static files used by a webapp.  Remember watching someone attach a web server we'd setup with read-only mounts over NFS. There's no way the client could change them to be writable, but they really tried. Seeing all the failures in the system log files, as they happened was funny and a little sad.

But for desktops, security is simpler.

---

### Post by ajgreeny on 2023-12-11
> **TheFu said:**
> I test each system, after patching, for the existence of /var/run/reboot-required.
If that file doesn't exist, I don't reboot.  Been doing this for decades, including 22.04 release (ubuntu and Mint).  If something changed after that, it is news to me.

It works on some Debian releases too ... or I'd never reboot my email gateway servers either.
Exactly how I've been upgrading/updating packages for a long time now.

I always run updates in terminal with command ```
sudo apt update && sudo apt full-upgrade && ls /var/run | grep reboot-required

``` which keeps me fully in touch with the status of things.

---

### Post by rusty.hinge on 2023-12-13
Can I assume from this thread that you folks are not receiving "System Upgrades" almost daily requiring a reboot.   Where the software update occurs during the reboot process nice Windows like message "Upgrade being installed.  Do Not turn of you Computer. "  

 I get no /var/run/reboot-required and needsrestart returns nothing. 

Cheers

---

### Post by ian-weisser on 2023-12-13
"*the software update occurs during the reboot process*" seems very different from "*updates/upgrades daily that require a reboot*." Each suggests a different trigger. We, seeing only the latter, have been assuming that the upgrade triggered the restart. Your latest update describes the opposite.

I doubt that we help you further without a clear, detailed description of the problem with a bit of context. We are not experiencing it. We cannot see it. We rely upon what you tell us.

---

### Post by TheFu on 2023-12-13
> **rusty.hinge said:**
> Can I assume from this thread that you folks are not receiving "System Upgrades" almost daily requiring a reboot.   Where the software update occurs during the reboot process nice Windows like message "Upgrade being installed.  Do Not turn of you Computer. "  

 I get no /var/run/reboot-required and needsrestart returns nothing. 

Cheers

I don't see any announcement that updates are needed and certainly don't have any automatically installed. These things are trivial to disable. Patching too often is a liability just like not patching often enough.

---

### Post by ajgreeny on 2023-12-14
> **TheFu said:**
> I don't see any announcement that updates are needed and certainly don't have any automatically installed. These things are trivial to disable. Patching too often is a liability just like not patching often enough.
I always remove the **unattended-upgrades** package as I want to know exactly what is going on and personally hate it when my OS decides to do something I have not asked it to do such as updating.
I also disable the update-notifier in the list of autostarted applications for more or less the same reason.
I do, however, update and upgrade everything frequently which is imperative if you want to keep your system running as risk free as possible.

---

