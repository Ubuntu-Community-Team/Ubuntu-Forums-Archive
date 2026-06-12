---
title: "comprehensive dist-upgrade"
date: 2020-12-02
forum: Ubuntu Development Version
---

### Post by zika on 2020-12-02
For a week now, 
```
 :~$ sudo apt dist-upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apport-symptoms aptdaemon-data gir1.2-goa-1.0 gir1.2-snapd-1 gir1.2-vte-2.91 libcolord-gtk1 libgl1-mesa-glx libglu1-mesa libgsound0 libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libpython3.8 librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-server-2.6-2 libxatracker2 libxvmc1
  mobile-broadband-provider-info network-manager-gnome python-apt-common python3-dateutil python3-debconf python3-defer python3-distro-info python3-gdbm python3-httplib2 python3-jeepney python3-keyring python3-launchpadlib python3-lazr.restfulclient python3-lazr.uri python3-problem-report python3-requests-unixsocket
  python3-secretstorage python3-simplejson python3-systemd python3-wadllib python3-xkit rygel x11-apps x11-session-utils xfonts-scalable xinit xinput xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati
  xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  apport apport-gtk aptdaemon apturl apturl-common command-not-found gnome-control-center language-selector-common language-selector-gnome libtss2-esys0 nautilus-share python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets python3-commandnotfound python3-distupgrade python3-software-properties
  python3-update-manager software-properties-common software-properties-gtk ubuntu-desktop ubuntu-desktop-minimal ubuntu-drivers-common ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-standard unattended-upgrades update-manager update-manager-core update-notifier update-notifier-common xorg
  xserver-xorg
The following NEW packages will be installed:
  activity-log-manager libfcitx-config4 libgeonames-common libgeonames0 libtimezonemap-data libtimezonemap1 libtss2-esys-3.0.2-0 libunity-control-center1 libunity-settings-daemon1 libzeitgeist-2.0-0 policykit-1-gnome unity-control-center unity-settings-daemon zeitgeist-core
The following packages will be upgraded:
  compizconfig-settings-manager fwupd gir1.2-rb-3.0 hplip hplip-data libhpmud0 libldb2 libpython3-stdlib librhythmbox-core10 libsane-hpaio libtalloc2 printer-driver-hpcups python3 python3-compizconfig python3-ldb python3-minimal python3-talloc rhythmbox rhythmbox-plugins
19 upgraded, 14 newly installed, 34 to remove and 0 not upgraded.
Need to get 18,5 MB of archives.
After this operation, 11,5 MB of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.
```
I do need xorg, or do I ?, I'm running on i3 and other simple DM's... ;)

---

### Post by TheFu on 2020-12-02
make a backup, let apt go.
Did you happen to install hwe updates?
Are you using wayland?

---

### Post by dino99 on 2020-12-02
If you accept the removal, then the system will be broken; needing a fresh system install.

---

### Post by zika on 2020-12-02
> **TheFu said:**
> make a backup, let apt go.
Did you happen to install hwe updates?
Are you using wayland?> **dino99 said:**
> If you accept the removal, then the system will be broken; needing a fresh system install.
I'll wait as I did so many times before. Eventhough I'm usin' Python 3.10, at this moment, this was just a HU for all of You. Some packages are not ready for Python 3.9 and some of us are not ready for zeitgeist and other changes (some of us still like Xserver) to come again at our door... ;)

---

### Post by TheFu on 2020-12-02
> **zika said:**
> I'll wait as I did so many times before. Eventhough I'm usin' Python 10, at this moment, this was just a HU for all of You. Some packages are not ready for Python 3.9 and some of us are not ready for zeitgeist and other changes (some of us still like Xserver) to come again at our door... ;)

Never replace the system version of python. Always use some other python environment manager and be certain to disable that setup when doing system administration work.

I have a feeling that python 10 won't be out or in development for some decades. Is that a typo?
The current OS python on 20.04 is 
```
$ python3 --version
Python 3.8.5

```

Just another example of why daily, automatic, versioned, backups that have been tested for restore are necessary.

---

### Post by zika on 2020-12-02
> **TheFu said:**
> Never replace the system version of python. Always use some other python environment manager and be certain to disable that setup when doing system administration work.

I have a feeling that python 10 won't be out or in development for some decades. Is that a typo?
The current OS python on 20.04 is 
```
$ python3 --version
Python 3.8.5

```
Just another example of why daily, automatic, versioned, backups that have been tested for restore are necessary.
OK, thank You... 
```
:~$ python3 --version 
Python 3.10.0a2
```
Still, it does not have any connection with important matter in this thread... ;)
Waiting for those packages to catch up with Python 3.9 and to see how to fight with ZeitGeist... ;)
Resolved, mistake was mine, I was using some PPA's that just now crossed edition line. Thank You all for bearing me... ;)

---

