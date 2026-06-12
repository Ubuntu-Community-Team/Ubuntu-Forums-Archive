---
title: "Update-mangler is mangled..."
date: 2023-03-14
forum: Ubuntu Development Version
---

### Post by Smask on 2023-03-14
u-m can't update the packages it show as upgradable and it doesn't show an error message,only that it can't calculate total download size. But if you start it in a terminal, it displays this on stdout:
```
Gtk-Message: 06:04:03.332: Failed to load module "appmenu-gtk-module"
/usr/lib/python3/dist-packages/gi/overrides/Gtk.py:1689: Warning: g_atomic_ref_count_dec: assertion 'old_value > 0' failed
  return _Gtk_main(*args, **kwargs)
required_download could not be calculated: E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64'
required_download could not be calculated: E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64'
required_download could not be calculated: E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64'
WARNING:root:directory '/var/lib/ubuntu-advantage/apt-esm/var/cache/apt/archives' does not exists
ERROR:root:free space check failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdatesAvailable.py", line 921, in on_button_install_clicked
    self.cache.checkFreeSpace()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeCache.py", line 1192, in checkFreeSpace
    for (dir, size) in [(archivedir, self.required_download),
                                     ^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MyCache.py", line 146, in required_download
    pm.get_archives(fetcher, self._list, self._records)
apt_pkg.Error: E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64'
```
Synaptic still works and I kept one package, ubuntu-settings, left in order to get an readable output compared to the wall of text it usually put out.

---

### Post by Claus7 on 2023-03-14
Hello,

under synaptic using gnome flashback I do not see the errors you are mentioning. I do not have ubuntu-settings as a kept package. Upgrade took place today as normal. This is the result of history log from synaptic:

> Commit Log for Tue Mar 14 12:31:19 2023


Upgraded the following packages:
gnome-initial-setup (44~beta-0ubuntu1) to 44~rc-0ubuntu1
language-pack-en (1:23.04+20230303) to 1:23.04+20230310
libdebconfclient0 (0.264ubuntu1) to 0.267ubuntu1
ubuntu-settings (23.04.2) to 23.04.3

Regards!

---

### Post by Smask on 2023-03-14
> **Claus7 said:**
> Hello,

under synaptic using gnome flashback I do not see the errors you are mentioning. I do not have ubuntu-settings as a kept package. Upgrade took place today as normal. This is the result of history log from synaptic:



Regards!
Sigh, it's update-manager that's borked, not synaptic. I updated all the packages, except one, ubuntu-settings, that I left as an example because I didn't want you to slog thru the wall-of-text that update-manager generates on stdout.

Anyhow here's update-manager with 26 packages to upgrade:
```
Gtk-Message: 04:12:09.274: Failed to load module "appmenu-gtk-module"
required_download could not be calculated: E:Can't find a source to download version '3.06-2ubuntu1' of 'sysvinit-utils:amd64', E:Can't find a source to download version '0.267ubuntu1' of 'libdebconfclient0:amd64', E:Can't find a source to download version '2.5.4-1ubuntu3' of 'libseccomp2:amd64', E:Can't find a source to download version '6.1.0-1ubuntu2' of 'iproute2:amd64', E:Can't find a source to download version '1.9.13p1-1ubuntu2' of 'sudo:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'libappstream4:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'appstream:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'apt-config-icons:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libgprofng0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-x86-64-linux-gnu:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-dev:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf-nobfd0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libbinutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-common:amd64', E:Can't find a source to download version '53-1' of 'gnome-shell-extension-appindicator:amd64', E:Can't find a source to download version '22.3.4+ds1-1' of 'libigdgmm12:amd64', E:Can't find a source to download version '23.1.2+dfsg1-1' of 'intel-media-va-driver:amd64', E:Can't find a source to download version '5.003+ds-1' of 'libsereal-decoder-perl:amd64', E:Can't find a source to download version '4.11.2-2' of 'python3-bs4:amd64', E:Can't find a source to download version '1.15.1-5build1' of 'python3-cffi-backend:amd64', E:Can't find a source to download version '1.0.23-2build3' of 'python3-smbc:amd64', E:Can't find a source to download version '2022.20230122-2' of 'texlive-base:amd64', E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64', E:Can't find a source to download version '3.0-13' of 'zip:amd64'
required_download could not be calculated: E:Can't find a source to download version '3.06-2ubuntu1' of 'sysvinit-utils:amd64', E:Can't find a source to download version '0.267ubuntu1' of 'libdebconfclient0:amd64', E:Can't find a source to download version '2.5.4-1ubuntu3' of 'libseccomp2:amd64', E:Can't find a source to download version '6.1.0-1ubuntu2' of 'iproute2:amd64', E:Can't find a source to download version '1.9.13p1-1ubuntu2' of 'sudo:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'libappstream4:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'appstream:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'apt-config-icons:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libgprofng0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-x86-64-linux-gnu:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-dev:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf-nobfd0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libbinutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-common:amd64', E:Can't find a source to download version '53-1' of 'gnome-shell-extension-appindicator:amd64', E:Can't find a source to download version '22.3.4+ds1-1' of 'libigdgmm12:amd64', E:Can't find a source to download version '23.1.2+dfsg1-1' of 'intel-media-va-driver:amd64', E:Can't find a source to download version '5.003+ds-1' of 'libsereal-decoder-perl:amd64', E:Can't find a source to download version '4.11.2-2' of 'python3-bs4:amd64', E:Can't find a source to download version '1.15.1-5build1' of 'python3-cffi-backend:amd64', E:Can't find a source to download version '1.0.23-2build3' of 'python3-smbc:amd64', E:Can't find a source to download version '2022.20230122-2' of 'texlive-base:amd64', E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64', E:Can't find a source to download version '3.0-13' of 'zip:amd64'
required_download could not be calculated: E:Can't find a source to download version '3.06-2ubuntu1' of 'sysvinit-utils:amd64', E:Can't find a source to download version '0.267ubuntu1' of 'libdebconfclient0:amd64', E:Can't find a source to download version '2.5.4-1ubuntu3' of 'libseccomp2:amd64', E:Can't find a source to download version '6.1.0-1ubuntu2' of 'iproute2:amd64', E:Can't find a source to download version '1.9.13p1-1ubuntu2' of 'sudo:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'libappstream4:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'appstream:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'apt-config-icons:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libgprofng0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-x86-64-linux-gnu:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-dev:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf-nobfd0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libbinutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-common:amd64', E:Can't find a source to download version '53-1' of 'gnome-shell-extension-appindicator:amd64', E:Can't find a source to download version '22.3.4+ds1-1' of 'libigdgmm12:amd64', E:Can't find a source to download version '23.1.2+dfsg1-1' of 'intel-media-va-driver:amd64', E:Can't find a source to download version '5.003+ds-1' of 'libsereal-decoder-perl:amd64', E:Can't find a source to download version '4.11.2-2' of 'python3-bs4:amd64', E:Can't find a source to download version '1.15.1-5build1' of 'python3-cffi-backend:amd64', E:Can't find a source to download version '1.0.23-2build3' of 'python3-smbc:amd64', E:Can't find a source to download version '2022.20230122-2' of 'texlive-base:amd64', E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64', E:Can't find a source to download version '3.0-13' of 'zip:amd64'
/usr/lib/python3/dist-packages/gi/overrides/Gtk.py:1689: Warning: g_atomic_ref_count_dec: assertion 'old_value > 0' failed
  return _Gtk_main(*args, **kwargs)
required_download could not be calculated: E:Can't find a source to download version '3.06-2ubuntu1' of 'sysvinit-utils:amd64', E:Can't find a source to download version '0.267ubuntu1' of 'libdebconfclient0:amd64', E:Can't find a source to download version '2.5.4-1ubuntu3' of 'libseccomp2:amd64', E:Can't find a source to download version '6.1.0-1ubuntu2' of 'iproute2:amd64', E:Can't find a source to download version '1.9.13p1-1ubuntu2' of 'sudo:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'libappstream4:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'appstream:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'apt-config-icons:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libgprofng0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-x86-64-linux-gnu:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-dev:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf-nobfd0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libbinutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-common:amd64', E:Can't find a source to download version '53-1' of 'gnome-shell-extension-appindicator:amd64', E:Can't find a source to download version '22.3.4+ds1-1' of 'libigdgmm12:amd64', E:Can't find a source to download version '23.1.2+dfsg1-1' of 'intel-media-va-driver:amd64', E:Can't find a source to download version '5.003+ds-1' of 'libsereal-decoder-perl:amd64', E:Can't find a source to download version '4.11.2-2' of 'python3-bs4:amd64', E:Can't find a source to download version '1.15.1-5build1' of 'python3-cffi-backend:amd64', E:Can't find a source to download version '1.0.23-2build3' of 'python3-smbc:amd64', E:Can't find a source to download version '2022.20230122-2' of 'texlive-base:amd64', E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64', E:Can't find a source to download version '3.0-13' of 'zip:amd64'
required_download could not be calculated: E:Can't find a source to download version '3.06-2ubuntu1' of 'sysvinit-utils:amd64', E:Can't find a source to download version '0.267ubuntu1' of 'libdebconfclient0:amd64', E:Can't find a source to download version '2.5.4-1ubuntu3' of 'libseccomp2:amd64', E:Can't find a source to download version '6.1.0-1ubuntu2' of 'iproute2:amd64', E:Can't find a source to download version '1.9.13p1-1ubuntu2' of 'sudo:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'libappstream4:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'appstream:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'apt-config-icons:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libgprofng0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-x86-64-linux-gnu:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-dev:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf-nobfd0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libbinutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-common:amd64', E:Can't find a source to download version '53-1' of 'gnome-shell-extension-appindicator:amd64', E:Can't find a source to download version '22.3.4+ds1-1' of 'libigdgmm12:amd64', E:Can't find a source to download version '23.1.2+dfsg1-1' of 'intel-media-va-driver:amd64', E:Can't find a source to download version '5.003+ds-1' of 'libsereal-decoder-perl:amd64', E:Can't find a source to download version '4.11.2-2' of 'python3-bs4:amd64', E:Can't find a source to download version '1.15.1-5build1' of 'python3-cffi-backend:amd64', E:Can't find a source to download version '1.0.23-2build3' of 'python3-smbc:amd64', E:Can't find a source to download version '2022.20230122-2' of 'texlive-base:amd64', E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64', E:Can't find a source to download version '3.0-13' of 'zip:amd64'
WARNING:root:directory '/var/lib/ubuntu-advantage/apt-esm/var/cache/apt/archives' does not exists
ERROR:root:free space check failed
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/UpdatesAvailable.py", line 921, in on_button_install_clicked
    self.cache.checkFreeSpace()
  File "/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeCache.py", line 1192, in checkFreeSpace
    for (dir, size) in [(archivedir, self.required_download),
                                     ^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MyCache.py", line 146, in required_download
    pm.get_archives(fetcher, self._list, self._records)
apt_pkg.Error: E:Can't find a source to download version '3.06-2ubuntu1' of 'sysvinit-utils:amd64', E:Can't find a source to download version '0.267ubuntu1' of 'libdebconfclient0:amd64', E:Can't find a source to download version '2.5.4-1ubuntu3' of 'libseccomp2:amd64', E:Can't find a source to download version '6.1.0-1ubuntu2' of 'iproute2:amd64', E:Can't find a source to download version '1.9.13p1-1ubuntu2' of 'sudo:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'libappstream4:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'appstream:amd64', E:Can't find a source to download version '0.16.1-1ubuntu1' of 'apt-config-icons:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libgprofng0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-x86-64-linux-gnu:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-dev:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libctf-nobfd0:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'libbinutils:amd64', E:Can't find a source to download version '2.40-2ubuntu3' of 'binutils-common:amd64', E:Can't find a source to download version '53-1' of 'gnome-shell-extension-appindicator:amd64', E:Can't find a source to download version '22.3.4+ds1-1' of 'libigdgmm12:amd64', E:Can't find a source to download version '23.1.2+dfsg1-1' of 'intel-media-va-driver:amd64', E:Can't find a source to download version '5.003+ds-1' of 'libsereal-decoder-perl:amd64', E:Can't find a source to download version '4.11.2-2' of 'python3-bs4:amd64', E:Can't find a source to download version '1.15.1-5build1' of 'python3-cffi-backend:amd64', E:Can't find a source to download version '1.0.23-2build3' of 'python3-smbc:amd64', E:Can't find a source to download version '2022.20230122-2' of 'texlive-base:amd64', E:Can't find a source to download version '23.04.3' of 'ubuntu-settings:amd64', E:Can't find a source to download version '3.0-13' of 'zip:amd64'

```

---

### Post by Claus7 on 2023-03-15
Hello,

I have invoked update-manager from terminal: Software updater started with the message "checking for updates". After a couple of seconds the message was: The software on this computer is up to date. Mind you that I have a "fresh" installation of lunar just four days ago.
I do not know if you could just re-install update manager or remove and install anew, yet I saw that it removes ubuntu-desktop as well which might not be a good idea.

Regards!

---

### Post by grahammechanical on 2023-03-15
For several days Software Updater has not be giving any updates. I did think this a bit strange on a development version heading for release day. But I did nothing about it until just now. Updating through the terminal I got a ton (or tonne) of updates. Including the Linux 6.1 kernel. I did notice that the terminal was reporting a much slower download rate than System Monitor was reporting. It seems that System Monitor was the accurate utility. Otherwise the download would have continued for the estimated hours that the terminal was reporting.

I have no idea what the problem is.

Regards

---

### Post by jbicha on 2023-03-16
Please file a bug.

```

ubuntu-bug update-manager

```

---

### Post by blueadept on 2023-03-17
I seem to have the same issue, reported the bug here:-

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/2012109](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/2012109)

---

### Post by grahammechanical on 2023-03-20
For the time being on 23.04 (development) I am updating using Advanced Options>Recovery mode. I do not have a problem getting an internet connection and running the update/upgrade commands.

Regards

---

### Post by cecilpierce on 2023-03-23
Update-manager is working again !

---

