---
title: "can not upgrade, error can not calculate upgrade"
date: 2014-02-22
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-02-22
unresolvable
How to fix?

found this in the log 

2014-02-22 09:59:01,065 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'

So how to tell what's broken?

---

### Post by sdowney717 on 2014-02-22
synaptic shows no broken packages

---

### Post by sdowney717 on 2014-02-22
could it be these 2 here?
They have been there for months.

some ppa list?

---

### Post by zika on 2014-02-22
```
sudo apt-get install -f
```in CLI...

---

### Post by ventrical on 2014-02-22
What method are you using to upgrade ?

edit: Just upgraded here using CLI .. no problems but then I don't have any ppas on THIS install.

---

### Post by sdowney717 on 2014-02-22
> **zika said:**
> ```
sudo apt-get install -f
```in CLI...

tried it nothing


scott@scott-P5QC:~$ sudo apt-get install -f
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
scott@scott-P5QC:~$

---

### Post by sdowney717 on 2014-02-22
> **ventrical said:**
> What method are you using to upgrade ?

edit: Just upgraded here using CLI .. no problems but then I don't have any ppas on THIS install.

terminal type in 

sudo update-manager -d

---

### Post by sdowney717 on 2014-02-22
significant or no?
```
scott@scott-P5QC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg-video-openchrome xserver-xorg-video-qxl
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by sdowney717 on 2014-02-22
upgrade log file
look for error

```
2014-02-22 10:20:00,558 INFO Using config files '['./DistUpgrade.cfg.precise']'
2014-02-22 10:20:00,558 INFO uname information: 'Linux scott-P5QC 3.12.0-031200-generic #201311031935 SMP Mon Nov 4 00:36:54 UTC 2013 x86_64'
2014-02-22 10:20:00,558 INFO apt version: '0.8.16~exp12ubuntu10.16'
2014-02-22 10:20:00,558 INFO release-upgrader version '0.210' started
2014-02-22 10:20:01,005 DEBUG Using 'DistUpgradeViewGtk3' view
2014-02-22 10:20:01,054 DEBUG aufsOptionsAndEnvironmentSetup()
2014-02-22 10:20:01,055 DEBUG using '/tmp/upgrade-rw-1S2QYY' as aufs_rw_dir
2014-02-22 10:20:01,055 DEBUG using '/tmp/upgrade-chroot-6KsWnd' as aufs chroot dir
2014-02-22 10:20:01,055 DEBUG enable dpkg --force-overwrite
2014-02-22 10:20:01,073 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2014-02-22 10:20:04,592 DEBUG lsb-release: 'precise'
2014-02-22 10:20:04,593 DEBUG _pythonSymlinkCheck run
2014-02-22 10:20:04,593 DEBUG openCache()
2014-02-22 10:20:04,593 DEBUG No such plugin directory: ./plugins
2014-02-22 10:20:04,594 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2014-02-22 10:20:04,594 DEBUG plugins for condition 'trustyPreCacheOpen' are '[]'
2014-02-22 10:20:04,594 DEBUG plugins for condition 'from_precisePreCacheOpen' are '[]'
2014-02-22 10:20:04,594 DEBUG quirks: running PreCacheOpen
2014-02-22 10:20:04,594 DEBUG running Quirks.PreCacheOpen
2014-02-22 10:20:05,386 DEBUG /openCache(), new cache size 62434
2014-02-22 10:20:05,386 DEBUG need_server_mode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2014-02-22 10:20:05,386 DEBUG checkViewDepends()
2014-02-22 10:20:05,386 DEBUG running doUpdate() (showErrors=False)
2014-02-22 10:20:06,346 DEBUG openCache()
2014-02-22 10:20:07,190 DEBUG /openCache(), new cache size 62434
2014-02-22 10:20:07,190 DEBUG doPostInitialUpdate
2014-02-22 10:20:07,190 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2014-02-22 10:20:07,190 DEBUG plugins for condition 'trustyPostInitialUpdate' are '[]'
2014-02-22 10:20:07,190 DEBUG plugins for condition 'from_precisePostInitialUpdate' are '[]'
2014-02-22 10:20:07,190 DEBUG quirks: running from_precisePostInitialUpdate
2014-02-22 10:20:07,208 DEBUG _test_and_warn_for_unity_3d_support: no unity running
2014-02-22 10:20:14,034 DEBUG Foreign: 
2014-02-22 10:20:14,034 DEBUG Obsolete: emblemize udisks2 gstreamer1.0-plugins-good gstreamer1.0-plugins-base indicator-notifications skype:i386 nvidia-screenlet gambas3-gb-qt4-ext libgstreamer-plugins-base1.0-0 gstreamer1.0-x linux-image-extra-3.6.9-030609-generic nautilus-advanced-menu librhythmbox-core6 linux-image-3.12.0-031200-generic libudisks2-0 gambas3-gb-image seafile indicator-ubuntuone webmin wuala libgegl-0.2-0 libbabl-0.1-0 gnome-shell-extensions-common libquicktimecine-cv gnome-shell-extensions-weather handbrake-gtk netflix-desktop gambas3-runtime cinelerra-cv linux-headers-3.6.9-030609 libboost-program-options1.49.0 cinnamon-translations opencpn nautilus-open-terminal-here faenza-icon-theme simplescreenrecorder linux-image-extra-3.5.0-18-generic virtualbox-4.2 gambas3-gb-sdl-sound acpibattery-screenlet teamviewer ubuntu-tweak nvidia-opencl-icd-304 linux-image-3.7.0-030700-generic libmusicbrainz5-0 gnome-shell-extensions libavcodec-extra gir1.2-gcr-3 gambas3-gb-desktop google-talkplugin libmlt5 simplescreenrecorder-lib libswresample0 linux-headers-3.7.0-030700-generic gambas3-gb-web oracle-java7-installer linux-image-3.6.9-030609-generic libgstreamer-plugins-good1.0-0 gambas3-gb-form-stock libcjs0c nautilus-open-as-root cinelerra-doc unsettings linux-headers-3.7.0-030700 libboost-filesystem1.49.0 libopus0 gnome-shell-extensions-user-theme linux-headers-3.6.9-030609-generic wine-browser-installer syncdrive nautilus-refresh libmpeg3cine-cv folderview-screenlet libboost-system1.49.0 wine-silverlight5.1-installer linux-image-extra-3.7.0-030700-generic gambas3-gb-qt4 gcr gir1.2-gck-1 cjs libguicast1-cv fuzzyclock-screenlet libvlccore7 wine-compholio:i386 google-chrome-stable gambas3-gb-form nautilus-gedit linux-headers-3.12.0-031200-generic linux-headers-3.12.0-031200 libgstreamer1.0-0
2014-02-22 10:20:14,035 DEBUG updateSourcesList()
2014-02-22 10:20:14,208 DEBUG rewriteSourcesList()
2014-02-22 10:20:14,211 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted'
2014-02-22 10:20:14,211 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted' updated to new dist
2014-02-22 10:20:14,212 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted'
2014-02-22 10:20:14,212 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted' updated to new dist
2014-02-22 10:20:14,212 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted'
2014-02-22 10:20:14,212 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted' updated to new dist
2014-02-22 10:20:14,212 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted'
2014-02-22 10:20:14,212 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted' updated to new dist
2014-02-22 10:20:14,212 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise universe'
2014-02-22 10:20:14,212 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty universe' updated to new dist
2014-02-22 10:20:14,212 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe'
2014-02-22 10:20:14,213 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe' updated to new dist
2014-02-22 10:20:14,213 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe'
2014-02-22 10:20:14,213 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe' updated to new dist
2014-02-22 10:20:14,213 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe'
2014-02-22 10:20:14,213 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe' updated to new dist
2014-02-22 10:20:14,213 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse'
2014-02-22 10:20:14,213 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse' updated to new dist
2014-02-22 10:20:14,213 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse'
2014-02-22 10:20:14,214 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse' updated to new dist
2014-02-22 10:20:14,214 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse'
2014-02-22 10:20:14,214 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse' updated to new dist
2014-02-22 10:20:14,214 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse'
2014-02-22 10:20:14,214 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse' updated to new dist
2014-02-22 10:20:14,214 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse'
2014-02-22 10:20:14,214 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse' updated to new dist
2014-02-22 10:20:14,214 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse'
2014-02-22 10:20:14,215 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse' updated to new dist
2014-02-22 10:20:14,215 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security main restricted'
2014-02-22 10:20:14,215 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security main restricted' updated to new dist
2014-02-22 10:20:14,215 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu precise-security main restricted'
2014-02-22 10:20:14,215 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted' updated to new dist
2014-02-22 10:20:14,215 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security universe'
2014-02-22 10:20:14,215 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security universe' updated to new dist
2014-02-22 10:20:14,215 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu precise-security universe'
2014-02-22 10:20:14,216 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu trusty-security universe' updated to new dist
2014-02-22 10:20:14,216 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu precise-security multiverse'
2014-02-22 10:20:14,216 DEBUG entry 'deb http://security.ubuntu.com/ubuntu trusty-security multiverse' updated to new dist
2014-02-22 10:20:14,216 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu precise-security multiverse'
2014-02-22 10:20:14,216 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse' updated to new dist
2014-02-22 10:20:14,259 DEBUG running doUpdate() (showErrors=True)
2014-02-22 10:20:28,334 DEBUG openCache()
2014-02-22 10:20:28,335 DEBUG failed to SystemUnLock() (E:Not locked) 
2014-02-22 10:20:33,892 DEBUG /openCache(), new cache size 70749
2014-02-22 10:20:33,893 DEBUG need_server_mode(): run in 'desktop' mode, (because of key deps for 'ubuntu-desktop')
2014-02-22 10:20:37,764 DEBUG Installing 'xserver-xorg-video-all' (Distro KeepInstalledPkgs rule)
2014-02-22 10:21:03,009 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
2014-02-22 10:21:03,009 DEBUG abort called
2014-02-22 10:21:03,019 DEBUG openCache()
2014-02-22 10:21:08,458 DEBUG /openCache(), new cache size 62434
2014-02-22 10:21:08,458 DEBUG enabling apt cron job
```

---

### Post by ventrical on 2014-02-22
I see the error .  Can't figure it out.

 Just  for the sake of it , try:

```

sudo apt-get update
sudo apt-get dist-upgrade

```


and/or reload from synaptic, then mark/apply. This worked for me once. I had the same error.

---

### Post by SeijiSensei on 2014-02-22
In another of your postings, I believe you said you are using a third-party PPA for X.  Why not just remove that PPA from your sources, run "sudo apt-get update" and use the repository versions?  I wouldn't be surprised if this is also a reason why you couldn't get VDPAU to work in SMPlayer.

I rarely use PPAs as they can cause all sorts of incompatibility problems like this one.  The only PPA I routinely add is the one for VirtualBox.

---

### Post by QDR06VV9 on 2014-02-22
> **ventrical said:**
> I see the error .  Can't figure it out.

 Just  for the sake of it , try:

```

sudo apt-get update
sudo apt-get dist-upgrade

```
You got in before me speed typer;)

---

### Post by ventrical on 2014-02-22
> **runrickus said:**
> You got in before me speed typer;)


Aye!:)lol

---

### Post by sdowney717 on 2014-02-22
nothing
```
scott@scott-P5QC:~$ sudo apt-get dist-upgrade
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  xserver-xorg-video-openchrome xserver-xorg-video-qxl
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
scott@scott-P5QC:~$ 
```

---

### Post by sdowney717 on 2014-02-22
> **SeijiSensei said:**
> In another of your postings, I believe you said you are using a third-party PPA for X.  Why not just remove that PPA from your sources, run "sudo apt-get update" and use the repository versions?  I wouldn't be surprised if this is also a reason why you couldn't get VDPAU to work in SMPlayer.

I rarely use PPAs as they can cause all sorts of incompatibility problems like this one.  The only PPA I routinely add is the one for VirtualBox.

I think I am. Would it be xorg-edgers?

What easy way to list the extra ppa's?
Are they in sources.lst?

---

### Post by sdowney717 on 2014-02-22
I disabled all the extra's
still can not calculate

```
scott@scott-P5QC:~$ grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/
/etc/apt/sources.list:
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
/etc/apt/sources.list:# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:# deb http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ubuntu precise partner
/etc/apt/sources.list:
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list:# deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:# deb-src http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list:# deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
/etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list:# deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
/etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
/etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
/etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list.save:# deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
/etc/apt/sources.list.d/cinelerra-ppa-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu precise main
/etc/apt/sources.list.d/cooperjona-stormcloud-precise.list.save:deb http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu precise main #Stormcloud Releases
/etc/apt/sources.list.d/diesch-testing-precise.list:# deb http://ppa.launchpad.net/diesch/testing/ubuntu precise main
/etc/apt/sources.list.d/diesch-testing-precise.list:# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu precise main
/etc/apt/sources.list.d/diesch-testing-precise.list.distUpgrade:# deb http://ppa.launchpad.net/diesch/testing/ubuntu precise main
/etc/apt/sources.list.d/diesch-testing-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu precise main
/etc/apt/sources.list.d/diesch-testing-precise.list.save:# deb http://ppa.launchpad.net/diesch/testing/ubuntu precise main
/etc/apt/sources.list.d/diesch-testing-precise.list.save:# deb-src http://ppa.launchpad.net/diesch/testing/ubuntu precise main
/etc/apt/sources.list.d/djcj-vlc-stable-precise.list:# deb http://ppa.launchpad.net/djcj/vlc-stable/ubuntu precise main
/etc/apt/sources.list.d/djcj-vlc-stable-precise.list:# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu precise main
/etc/apt/sources.list.d/djcj-vlc-stable-precise.list.distUpgrade:# deb http://ppa.launchpad.net/djcj/vlc-stable/ubuntu precise main
/etc/apt/sources.list.d/djcj-vlc-stable-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu precise main
/etc/apt/sources.list.d/djcj-vlc-stable-precise.list.save:# deb http://ppa.launchpad.net/djcj/vlc-stable/ubuntu precise main
/etc/apt/sources.list.d/djcj-vlc-stable-precise.list.save:deb-src http://ppa.launchpad.net/djcj/vlc-stable/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list:# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.distUpgrade:# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:# deb http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/ehoover-compholio-precise.list.save:# deb-src http://ppa.launchpad.net/ehoover/compholio/ubuntu precise main
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list:# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.distUpgrade:# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.save:# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/gnome3-team-gnome3-precise.list.save:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.distUpgrade:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:# deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-earth.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list:# deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-earth.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list.distUpgrade:# deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-earth.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-earth.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-earth.list.save:# deb http://dl.google.com/linux/earth/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list:# deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.distUpgrade:# deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.save:# deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list:# deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list:# deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.distUpgrade:# deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.save:# deb http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/gwendal-lebihan-dev-cinnamon-stable-precise.list.save:# deb-src http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
/etc/apt/sources.list.d/hizo-logiciels-precise.list:# deb http://ppa.launchpad.net/hizo/logiciels/ubuntu precise main
/etc/apt/sources.list.d/hizo-logiciels-precise.list:# deb-src http://ppa.launchpad.net/hizo/logiciels/ubuntu precise main
/etc/apt/sources.list.d/hizo-logiciels-precise.list.distUpgrade:# deb http://ppa.launchpad.net/hizo/logiciels/ubuntu precise main
/etc/apt/sources.list.d/hizo-logiciels-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/hizo/logiciels/ubuntu precise main
/etc/apt/sources.list.d/hizo-logiciels-precise.list.save:# deb http://ppa.launchpad.net/hizo/logiciels/ubuntu precise main
/etc/apt/sources.list.d/hizo-logiciels-precise.list.save:# deb-src http://ppa.launchpad.net/hizo/logiciels/ubuntu precise main
/etc/apt/sources.list.d/jconti-recent-notifications-precise.list:# deb http://ppa.launchpad.net/jconti/recent-notifications/ubuntu precise main
/etc/apt/sources.list.d/jconti-recent-notifications-precise.list:# deb-src http://ppa.launchpad.net/jconti/recent-notifications/ubuntu precise main
/etc/apt/sources.list.d/jconti-recent-notifications-precise.list.distUpgrade:# deb http://ppa.launchpad.net/jconti/recent-notifications/ubuntu precise main
/etc/apt/sources.list.d/jconti-recent-notifications-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/jconti/recent-notifications/ubuntu precise main
/etc/apt/sources.list.d/jconti-recent-notifications-precise.list.save:# deb http://ppa.launchpad.net/jconti/recent-notifications/ubuntu precise main
/etc/apt/sources.list.d/jconti-recent-notifications-precise.list.save:# deb-src http://ppa.launchpad.net/jconti/recent-notifications/ubuntu precise main
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-precise.list:# deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu precise main
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-precise.list:# deb-src http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu precise main
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-precise.list.distUpgrade:# deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu precise main
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu precise main
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-precise.list.save:# deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu precise main
/etc/apt/sources.list.d/jon-severinsson-ffmpeg-precise.list.save:# deb-src http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu precise main
/etc/apt/sources.list.d/kazam-team-stable-series-precise.list:# deb http://ppa.launchpad.net/kazam-team/stable-series/ubuntu precise main
/etc/apt/sources.list.d/kazam-team-stable-series-precise.list:# deb-src http://ppa.launchpad.net/kazam-team/stable-series/ubuntu precise main
/etc/apt/sources.list.d/kazam-team-stable-series-precise.list.distUpgrade:# deb http://ppa.launchpad.net/kazam-team/stable-series/ubuntu precise main
/etc/apt/sources.list.d/kazam-team-stable-series-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/kazam-team/stable-series/ubuntu precise main
/etc/apt/sources.list.d/kazam-team-stable-series-precise.list.save:# deb http://ppa.launchpad.net/kazam-team/stable-series/ubuntu precise main
/etc/apt/sources.list.d/kazam-team-stable-series-precise.list.save:# deb-src http://ppa.launchpad.net/kazam-team/stable-series/ubuntu precise main
/etc/apt/sources.list.d/kazam-team-unstable-series-precise.list.save:deb-src http://ppa.launchpad.net/kazam-team/unstable-series/ubuntu precise main
/etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-precise.list:# deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu precise main
/etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-precise.list:# deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu precise main
/etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-precise.list.distUpgrade:# deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu precise main
/etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu precise main
/etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-precise.list.save:# deb http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu precise main
/etc/apt/sources.list.d/maarten-baert-simplescreenrecorder-precise.list.save:# deb-src http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu precise main
/etc/apt/sources.list.d/me-davidsansome-clementine-precise.list:# deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu precise main
/etc/apt/sources.list.d/me-davidsansome-clementine-precise.list:# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu precise main
/etc/apt/sources.list.d/me-davidsansome-clementine-precise.list.distUpgrade:# deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu precise main
/etc/apt/sources.list.d/me-davidsansome-clementine-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu precise main
/etc/apt/sources.list.d/me-davidsansome-clementine-precise.list.save:# deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu precise main
/etc/apt/sources.list.d/me-davidsansome-clementine-precise.list.save:# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu precise main
/etc/apt/sources.list.d/mqchael-pipelight-precise.list:# deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main
/etc/apt/sources.list.d/mqchael-pipelight-precise.list:# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main
/etc/apt/sources.list.d/mqchael-pipelight-precise.list.distUpgrade:# deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main
/etc/apt/sources.list.d/mqchael-pipelight-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main
/etc/apt/sources.list.d/mqchael-pipelight-precise.list.save:# deb http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main
/etc/apt/sources.list.d/mqchael-pipelight-precise.list.save:# deb-src http://ppa.launchpad.net/mqchael/pipelight/ubuntu precise main
/etc/apt/sources.list.d/nae-team-ppa-precise.list:# deb http://ppa.launchpad.net/nae-team/ppa/ubuntu precise main
/etc/apt/sources.list.d/nae-team-ppa-precise.list:# deb-src http://ppa.launchpad.net/nae-team/ppa/ubuntu precise main
/etc/apt/sources.list.d/nae-team-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/nae-team/ppa/ubuntu precise main
/etc/apt/sources.list.d/nae-team-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/nae-team/ppa/ubuntu precise main
/etc/apt/sources.list.d/nae-team-ppa-precise.list.save:# deb http://ppa.launchpad.net/nae-team/ppa/ubuntu precise main
/etc/apt/sources.list.d/nae-team-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/nae-team/ppa/ubuntu precise main
/etc/apt/sources.list.d/nemh-gambas3-precise.list:# deb http://ppa.launchpad.net/nemh/gambas3/ubuntu precise main
/etc/apt/sources.list.d/nemh-gambas3-precise.list:# deb-src http://ppa.launchpad.net/nemh/gambas3/ubuntu precise main
/etc/apt/sources.list.d/nemh-gambas3-precise.list.distUpgrade:# deb http://ppa.launchpad.net/nemh/gambas3/ubuntu precise main
/etc/apt/sources.list.d/nemh-gambas3-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/nemh/gambas3/ubuntu precise main
/etc/apt/sources.list.d/nemh-gambas3-precise.list.save:# deb http://ppa.launchpad.net/nemh/gambas3/ubuntu precise main
/etc/apt/sources.list.d/nemh-gambas3-precise.list.save:# deb-src http://ppa.launchpad.net/nemh/gambas3/ubuntu precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list:# deb http://ppa.launchpad.net/noobslab/indicators/ubuntu precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list:# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list.distUpgrade:# deb http://ppa.launchpad.net/noobslab/indicators/ubuntu precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list.save:# deb http://ppa.launchpad.net/noobslab/indicators/ubuntu precise main
/etc/apt/sources.list.d/noobslab-indicators-precise.list.save:# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu precise main
/etc/apt/sources.list.d/noobslab-pear-apps-precise.list:# deb http://ppa.launchpad.net/noobslab/pear-apps/ubuntu precise main
/etc/apt/sources.list.d/noobslab-pear-apps-precise.list:# deb-src http://ppa.launchpad.net/noobslab/pear-apps/ubuntu precise main
/etc/apt/sources.list.d/noobslab-pear-apps-precise.list.distUpgrade:# deb http://ppa.launchpad.net/noobslab/pear-apps/ubuntu precise main
/etc/apt/sources.list.d/noobslab-pear-apps-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/noobslab/pear-apps/ubuntu precise main
/etc/apt/sources.list.d/noobslab-pear-apps-precise.list.save:# deb http://ppa.launchpad.net/noobslab/pear-apps/ubuntu precise main
/etc/apt/sources.list.d/noobslab-pear-apps-precise.list.save:# deb-src http://ppa.launchpad.net/noobslab/pear-apps/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list:# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.distUpgrade:# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save:# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list.save:# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu precise main
/etc/apt/sources.list.d/ricotz-testing-precise.list.save:deb-src http://ppa.launchpad.net/ricotz/testing/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list:# deb http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list:# deb-src http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.distUpgrade:# deb http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.save:# deb http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/rye-ubuntuone-extras-precise.list.save:# deb-src http://ppa.launchpad.net/rye/ubuntuone-extras/ubuntu precise main
/etc/apt/sources.list.d/samrog131-ppa-precise.list:# deb http://ppa.launchpad.net/samrog131/ppa/ubuntu precise main
/etc/apt/sources.list.d/samrog131-ppa-precise.list:# deb-src http://ppa.launchpad.net/samrog131/ppa/ubuntu precise main
/etc/apt/sources.list.d/samrog131-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/samrog131/ppa/ubuntu precise main
/etc/apt/sources.list.d/samrog131-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/samrog131/ppa/ubuntu precise main
/etc/apt/sources.list.d/samrog131-ppa-precise.list.save:# deb http://ppa.launchpad.net/samrog131/ppa/ubuntu precise main
/etc/apt/sources.list.d/samrog131-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/samrog131/ppa/ubuntu precise main
/etc/apt/sources.list.d/screenlets-ppa-precise.list:# deb http://ppa.launchpad.net/screenlets/ppa/ubuntu precise main
/etc/apt/sources.list.d/screenlets-ppa-precise.list:# deb-src http://ppa.launchpad.net/screenlets/ppa/ubuntu precise main
/etc/apt/sources.list.d/screenlets-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/screenlets/ppa/ubuntu precise main
/etc/apt/sources.list.d/screenlets-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/screenlets/ppa/ubuntu precise main
/etc/apt/sources.list.d/screenlets-ppa-precise.list.save:# deb http://ppa.launchpad.net/screenlets/ppa/ubuntu precise main
/etc/apt/sources.list.d/screenlets-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/screenlets/ppa/ubuntu precise main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list:# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list:# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.distUpgrade:# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.save:# deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
/etc/apt/sources.list.d/stebbins-handbrake-releases-precise.list.save:# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu precise main
/etc/apt/sources.list.d/sunab-kdenlive-release-precise.list:# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
/etc/apt/sources.list.d/sunab-kdenlive-release-precise.list:# deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
/etc/apt/sources.list.d/sunab-kdenlive-release-precise.list.distUpgrade:# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
/etc/apt/sources.list.d/sunab-kdenlive-release-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
/etc/apt/sources.list.d/sunab-kdenlive-release-precise.list.save:# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
/etc/apt/sources.list.d/sunab-kdenlive-release-precise.list.save:# deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main
/etc/apt/sources.list.d/tiheum-equinox-precise.list:# deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Include the Faenza icon set
/etc/apt/sources.list.d/tiheum-equinox-precise.list.distUpgrade:# deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Include the Faenza icon set
/etc/apt/sources.list.d/tiheum-equinox-precise.list.save:# deb http://ppa.launchpad.net/tiheum/equinox/ubuntu precise main #Include the Faenza icon set
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list:# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list:# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.distUpgrade:# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save:# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-precise.list.save:# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-gnome3-precise.list:# deb http://ppa.launchpad.net/webupd8team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-gnome3-precise.list:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-gnome3-precise.list.distUpgrade:# deb http://ppa.launchpad.net/webupd8team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-gnome3-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-gnome3-precise.list.save:# deb http://ppa.launchpad.net/webupd8team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-gnome3-precise.list.save:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:# deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.distUpgrade:# deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:# deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
/etc/apt/sources.list.d/wuala.list:# Wuala repository
/etc/apt/sources.list.d/wuala.list:# deb http://repo.wuala.com stable main
/etc/apt/sources.list.d/wuala.list.distUpgrade:# Wuala repository
/etc/apt/sources.list.d/wuala.list.distUpgrade:# deb http://repo.wuala.com stable main
/etc/apt/sources.list.d/wuala.list.save:# Wuala repository
/etc/apt/sources.list.d/wuala.list.save:# deb http://repo.wuala.com stable main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list:# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list:# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.distUpgrade:# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.distUpgrade:# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.save:# deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.save:# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu precise main
scott@scott-P5QC:~$ 

```




```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

---

### Post by ventrical on 2014-02-22
Look at this link:

[http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12213652#post12213652](http://ubuntuforums.org/showthread.php?t=1970289&page=2&p=12213652#post12213652)

and look at item #13 on this link:

[http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873](http://ubuntuforums.org/showthread.php?t=1970289&p=11893873#post11893873)

---

### Post by sdowney717 on 2014-02-22
Ok, so a list but is one of these the problem, which one?
```
scott@scott-P5QC:~$    if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; else echo -e "\n\nEmpty or inexistent PPA directory\n\n"; fi


PPA dir   exists and is not empty


# ppacinelerra-ppa/ppa precise 
# ppacinelerra-ppa/ppa precise 
# ppacinelerra-ppa/ppa precise 
ppacooperjona/stormcloud precise  #Stormcloud Releases
# ppadiesch/testing precise 
# ppadiesch/testing precise 
# ppadiesch/testing precise 
# ppadjcj/vlc-stable precise 
# ppadjcj/vlc-stable precise 
# ppadjcj/vlc-stable precise 
# ppaehoover/compholio precise 
# ppaehoover/compholio precise 
# ppaehoover/compholio precise 
# ppagnome3-team/gnome3 precise 
# ppagnome3-team/gnome3 precise 
# ppagnome3-team/gnome3 precise 
# dl.google.com/linux/chrome/deb/ stable 
# dl.google.com/linux/chrome/deb/ stable 
# dl.google.com/linux/chrome/deb/ stable 
# dl.google.com/linux/earth/deb/ stable 
# dl.google.com/linux/earth/deb/ stable 
# dl.google.com/linux/earth/deb/ stable 
# dl.google.com/linux/talkplugin/deb/ stable 
# dl.google.com/linux/talkplugin/deb/ stable 
# dl.google.com/linux/talkplugin/deb/ stable 
# ppagwendal-lebihan-dev/cinnamon-stable precise 
# ppagwendal-lebihan-dev/cinnamon-stable precise 
# ppagwendal-lebihan-dev/cinnamon-stable precise 
# ppahizo/logiciels precise 
# ppahizo/logiciels precise 
# ppahizo/logiciels precise 
# ppajconti/recent-notifications precise 
# ppajconti/recent-notifications precise 
# ppajconti/recent-notifications precise 
# ppajon-severinsson/ffmpeg precise 
# ppajon-severinsson/ffmpeg precise 
# ppajon-severinsson/ffmpeg precise 
# ppakazam-team/stable-series precise 
# ppakazam-team/stable-series precise 
# ppakazam-team/stable-series precise 
# ppamaarten-baert/simplescreenrecorder precise 
# ppamaarten-baert/simplescreenrecorder precise 
# ppamaarten-baert/simplescreenrecorder precise 
# ppame-davidsansome/clementine precise 
# ppame-davidsansome/clementine precise 
# ppame-davidsansome/clementine precise 
# ppamqchael/pipelight precise 
# ppamqchael/pipelight precise 
# ppamqchael/pipelight precise 
# ppanae-team/ppa precise 
# ppanae-team/ppa precise 
# ppanae-team/ppa precise 
# ppanemh/gambas3 precise 
# ppanemh/gambas3 precise 
# ppanemh/gambas3 precise 
# ppanoobslab/indicators precise 
# ppanoobslab/indicators precise 
# ppanoobslab/indicators precise 
# ppanoobslab/pear-apps precise 
# ppanoobslab/pear-apps precise 
# ppanoobslab/pear-apps precise 
# ppaotto-kesselgulasch/gimp precise 
# ppaotto-kesselgulasch/gimp precise 
# ppaotto-kesselgulasch/gimp precise 
# pparyeone-extras/ubuntu precise 
# pparyeone-extras/ubuntu precise 
# pparyeone-extras/ubuntu precise 
# ppasamrog131/ppa precise 
# ppasamrog131/ppa precise 
# ppasamrog131/ppa precise 
# ppascreenlets/ppa precise 
# ppascreenlets/ppa precise 
# ppascreenlets/ppa precise 
# ppastebbins/handbrake-releases precise 
# ppastebbins/handbrake-releases precise 
# ppastebbins/handbrake-releases precise 
# ppasunab/kdenlive-release precise 
# ppasunab/kdenlive-release precise 
# ppasunab/kdenlive-release precise 
# ppatiheum/equinox precise  #Include the Faenza icon set
# ppatiheum/equinox precise  #Include the Faenza icon set
# ppatiheum/equinox precise  #Include the Faenza icon set
# ppaubuntu-x-swat/x-updates precise 
# ppaubuntu-x-swat/x-updates precise 
# ppaubuntu-x-swat/x-updates precise 
# ppawebupd8team/gnome3 precise 
# ppawebupd8team/gnome3 precise 
# ppawebupd8team/gnome3 precise 
# ppawebupd8team/java precise 
# ppawebupd8team/java precise 
# ppawebupd8team/java precise 
# repo.wuala.com stable 
# repo.wuala.com stable 
# repo.wuala.com stable 
# ppaxorg-edgers/ppa precise 
# ppaxorg-edgers/ppa precise 
# ppaxorg-edgers/ppa precise 
PPA list saved at /home/scott/ppa-sources.list

```

---

### Post by ventrical on 2014-02-22
This one is not commented out:

```

ppacooperjona/stormcloud precise  #Stormcloud Releases

```

but I don't think that's the problem. Hmnnn...

---

### Post by sdowney717 on 2014-02-22
I saw that, anyway tried to remove ppa and can not?

Am I doing it right?

```
scott@scott-P5QC:~$ sudo ppa-purge ppa:ppacooperjona/stormcloud
[sudo] password for scott: 
Updating packages lists
PPA to be removed: ppacooperjona stormcloud
Warning:  Could not find package list for PPA: ppacooperjona stormcloud
scott@scott-P5QC:~$ sudo ppa-purge ppa:ppacooperjona
Updating packages lists
PPA to be removed: ppa:ppacooperjona ppa:ppacooperjona
Warning:  Could not find package list for PPA: ppa:ppacooperjona 
ppa:ppacooperjona
scott@scott-P5QC:~$ sudo ppa-purge ppa:ppacooperjona-ppa
Updating packages lists
PPA to be removed: ppa:ppacooperjona-ppa ppa:ppacooperjona-ppa
Warning:  Could not find package list for PPA: ppa:ppacooperjona-ppa 
ppa:ppacooperjona-ppa
scott@scott-P5QC:~$ sudo ppa-purge ppacooperjona/stormcloud
Updating packages lists
PPA to be removed: ppacooperjona/stormcloud ppa
Warning:  Could not find package list for PPA: ppacooperjona/stormcloud ppa
scott@scott-P5QC:~$ sudo update-manager -d
authenticate 'trusty.tar.gz' against 'trusty.tar.gz.gpg' 
extracting 'trusty.tar.gz'
scott@scott-P5QC:~$ sudo ppa-purge  ppadiesch/testing
Updating packages lists
PPA to be removed: ppadiesch/testing ppa
Warning:  Could not find package list for PPA: ppadiesch/testing ppa
scott@scott-P5QC:~$ sudo apt-add-repository --remove ppa:ppadiesch/testing
Cannot access PPA (https://launchpad.net/api/1.0/~ppadiesch/+archive/testing) to get PPA information, please check your internet connection.
scott@scott-P5QC:~$ sudo apt-add-repository --remove ppa:ppadiesch/testing/ppa
Cannot access PPA (https://launchpad.net/api/1.0/~ppadiesch/+archive/testing/ppa) to get PPA information, please check your internet connection.
scott@scott-P5QC:~$ 

```

---

### Post by ventrical on 2014-02-22
Read here ..

[http://askubuntu.com/questions/307/how-can-ppas-be-removed](http://askubuntu.com/questions/307/how-can-ppas-be-removed)

---

### Post by zika on 2014-02-22
We (at least I) did write numeorous times that XorgEdgers should never be on during version upgrade... It (almost) all the time make problem like this You have... I've been burned twice and after licking those burns I've learned my lesson and shared it in U+1 instantly both times...
I'm afraid it is late to do:```
sudo ppa-purge **ppa:xorg-edgers/ppa**
```but...
Reason for this is simple: version numbers...

---

### Post by zika on 2014-02-22
> **sdowney717 said:**
> synaptic shows no broken packagesThere are no brocken packages just missmatched version numbers...

---

### Post by zika on 2014-02-22
> **ventrical said:**
> Read here ..

[http://askubuntu.com/questions/307/how-can-ppas-be-removed](http://askubuntu.com/questions/307/how-can-ppas-be-removed)@OP Do not use```
add-apt-repository --remove
```as it will just remove it from the list and not revert packages that should be reverted bevore version upgrade...
There is a bumpy lane that You could use: turn xorg-edgers off and reinstall two packages mentioned. But. if You did not try that lane already, better do not go there... I would try ppa-purge first... Do not expect roses on that road either...

---

### Post by sdowney717 on 2014-02-22
Can not remove the PPA, but it is in the list.
foobar.
??????
```
scott@scott-P5QC:~$ sudo ppa-purge ppa:xorg-edgers/ppa
[sudo] password for scott: 
Updating packages lists
PPA to be removed: xorg-edgers ppa
Warning:  Could not find package list for PPA: xorg-edgers ppa
scott@scott-P5QC:~$
```


```
scott@scott-P5QC:~$ scott@scott-P5QC:~$    if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; else echo -e "\n\nEmpty or inexistent PPA directory\n\n"; fi
bash: syntax error near unexpected token `then'
scott@scott-P5QC:~$ 
scott@scott-P5QC:~$  if  [[ -d /etc/apt/sources.list.d && $(ls -l   /etc/apt/sources.list.d/* | wc -l) -gt 0 ]]; then echo -e "\n\nPPA dir   exists and is not empty\n\n"; for PPA_FILE in $(ls   /etc/apt/sources.list.d/*); do cat ${PPA_FILE} | grep "deb http" | sed   -e 's|deb http:\/\/||' | sed -e 's|.launchpad.net/||' | sed -e   's|/ubuntu||' | sed -e 's|natty||' | sed -e 's|maverick||' | sed -e   's|oneiric||' | sed -e 's|main||' | tee -a $HOME/ppa-sources.list;  done;  echo "PPA list saved at $HOME/ppa-sources.list"; else echo -e "\n\nEmpty or inexistent PPA directory\n\n"; fi


PPA dir   exists and is not empty


# ppacinelerra-ppa/ppa precise 
# ppacinelerra-ppa/ppa precise 
ppacooperjona/stormcloud precise  #Stormcloud Releases
# ppadiesch/testing precise 
# ppadiesch/testing precise 
# ppadiesch/testing precise 
# ppadjcj/vlc-stable precise 
# ppadjcj/vlc-stable precise 
# ppadjcj/vlc-stable precise 
# ppaehoover/compholio precise 
# ppaehoover/compholio precise 
# ppaehoover/compholio precise 
# ppagnome3-team/gnome3 precise 
# ppagnome3-team/gnome3 precise 
# ppagnome3-team/gnome3 precise 
# dl.google.com/linux/chrome/deb/ stable 
# dl.google.com/linux/chrome/deb/ stable 
# dl.google.com/linux/chrome/deb/ stable 
# dl.google.com/linux/talkplugin/deb/ stable 
# dl.google.com/linux/talkplugin/deb/ stable 
# dl.google.com/linux/talkplugin/deb/ stable 
# ppagwendal-lebihan-dev/cinnamon-stable precise 
# ppagwendal-lebihan-dev/cinnamon-stable precise 
# ppagwendal-lebihan-dev/cinnamon-stable precise 
# ppahizo/logiciels precise 
# ppahizo/logiciels precise 
# ppahizo/logiciels precise 
# ppajconti/recent-notifications precise 
# ppajconti/recent-notifications precise 
# ppajconti/recent-notifications precise 
# ppajon-severinsson/ffmpeg precise 
# ppajon-severinsson/ffmpeg precise 
# ppakazam-team/stable-series precise 
# ppakazam-team/stable-series precise 
# ppamaarten-baert/simplescreenrecorder precise 
# ppamaarten-baert/simplescreenrecorder precise 
# ppamaarten-baert/simplescreenrecorder precise 
# ppame-davidsansome/clementine precise 
# ppame-davidsansome/clementine precise 
# ppame-davidsansome/clementine precise 
# ppamqchael/pipelight precise 
# ppamqchael/pipelight precise 
# ppamqchael/pipelight precise 
# ppanae-team/ppa precise 
# ppanae-team/ppa precise 
# ppanae-team/ppa precise 
# ppanemh/gambas3 precise 
# ppanemh/gambas3 precise 
# ppanemh/gambas3 precise 
# ppanoobslab/indicators precise 
# ppanoobslab/indicators precise 
# ppanoobslab/indicators precise 
# ppanoobslab/pear-apps precise 
# ppanoobslab/pear-apps precise 
# ppanoobslab/pear-apps precise 
# ppaotto-kesselgulasch/gimp precise 
# ppaotto-kesselgulasch/gimp precise 
# ppaotto-kesselgulasch/gimp precise 
# pparyeone-extras/ubuntu precise 
# pparyeone-extras/ubuntu precise 
# pparyeone-extras/ubuntu precise 
# ppasamrog131/ppa precise 
# ppasamrog131/ppa precise 
# ppascreenlets/ppa precise 
# ppascreenlets/ppa precise 
# ppastebbins/handbrake-releases precise 
# ppastebbins/handbrake-releases precise 
# ppastebbins/handbrake-releases precise 
# ppasunab/kdenlive-release precise 
# ppasunab/kdenlive-release precise 
# ppasunab/kdenlive-release precise 
# ppatiheum/equinox precise  #Include the Faenza icon set
# ppatiheum/equinox precise  #Include the Faenza icon set
# ppatiheum/equinox precise  #Include the Faenza icon set
# ppaubuntu-x-swat/x-updates precise 
# ppaubuntu-x-swat/x-updates precise 
# ppaubuntu-x-swat/x-updates precise 
# ppawebupd8team/gnome3 precise 
# ppawebupd8team/gnome3 precise 
# ppawebupd8team/gnome3 precise 
# ppawebupd8team/java precise 
# ppawebupd8team/java precise 
# ppawebupd8team/java precise 
# ppaxorg-edgers/ppa precise 
# ppaxorg-edgers/ppa precise 
PPA list saved at /home/scott/ppa-sources.list
scott@scott-P5QC:~$ sudo ppa-purge ppa:xorg-edgers/ppa
[sudo] password for scott: 
Updating packages lists
PPA to be removed: xorg-edgers ppa
Warning:  Could not find package list for PPA: xorg-edgers ppa
scott@scott-P5QC:~$ 
```

---

### Post by sdowney717 on 2014-02-22
pic of the package list, it is in the folder.
How about deleting that xorg one manually in the folder?

---

### Post by monkeybrain20122 on 2014-02-22
If you have ppas upgrade won't work because your software packages now have versions differ from what the updater expects. Also you have to remove your Nvidia driver.

I would just back up my data and do a clean install, it saves you time and troubles in the future. Clean install takes ~ 20 minutes and upgrade hours. In the future make a separate /home partition.

---

### Post by sdowney717 on 2014-02-22
I have a separate /home partition.
All I wanted to do was click and let it do its thing. 
Now it will be more work.

First time I have not been able to upgrade, been using linux since the hardy version.

---

### Post by sdowney717 on 2014-02-22
First time I have not been able to upgrade, been using linux since the hardy version.

I have always had numerous PPA's and the linux driver and was never a problem.

---

### Post by zika on 2014-02-22
> **sdowney717 said:**
> Can not remove the PPA, but it is in the list.
foobar.
??????
```
scott@scott-P5QC:~$ sudo ppa-purge ppa:xorg-edgers/ppa
[sudo] password for scott: 
Updating packages lists
PPA to be removed: xorg-edgers ppa
Warning:  Could not find package list for PPA: xorg-edgers ppa
scott@scott-P5QC:~$
```Not a surprise it can not find package list... In order to use ppa-purge You have to have proper branch of ppa in appropriate file in /etc/apt.sources.list.d and You have to have it turned on in order for update process to find packages that need to be reinstalled (downgraded or whatever...) I'm sure that You have file and in it XE is turned off (i.e. commented out)... So, that is easy part of passing that bridge...

---

### Post by monkeybrain20122 on 2014-02-22
> **sdowney717 said:**
> I have a separate /home partition.
All I wanted to do was click and let it do its thing. 
Now it will be more work.

First time I have not been able to upgrade, been using linux since the hardy version.

If you have a separate /home then it is even easier. Just make a list of software you installed [http://askubuntu.com/questions/17823/how-to-list-all-installed-packages](http://askubuntu.com/questions/17823/how-to-list-all-installed-packages) and when install, do not format your /home. 20 minutes later you use the list to reinstall all software (making changes if necessary to reflect release changes) and that's it. (Since Trusty is a pre-release it may be better to install the software manually, but that wouldn't take long, much faster than doing upgrade)

It may be "more work" then pressing a button but not much more and saves you much work for future trouble shootings. You said you always upgrade, that may explain  why you have many strange problems which are hard to diagnose. :)

**Edited**: You are doing more work right here. By the time you figure out the problem you post on this thread (if you do) so you can proceed with the upgrade (no guarantee that it will finish without error) I would have a a spanking new 14.04 and playing if I do a clean install. ;)

---

### Post by ventrical on 2014-02-22
Try :

```

sudo apt-get autoremove

```


and see if that cleans up some of those lists. Again, I had a similar problem and I worked at it and worked at it and then I had to do something with updating the xapian list (forget) but that fixed the other ppa problem I had back way when.

Edit: Looks like zika has the right method to get somewhere with this. Listen there.

---

### Post by sdowney717 on 2014-02-22
Ok, reenabled it and something went wrong

So what to do?
```
Disabling xorg-edgers PPA from 
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [amd64]) for 'libcairo2'
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [i386]) for 'libcairo2:i386'
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [amd64]) for 'libcairo-gobject2'
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [i386]) for 'libcairo-gobject2:i386'
Selected version '2.4.46-1ubuntu0.0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'libdrm-nouveau1a'
Selected version '2.4.46-1ubuntu0.0.0.1' (Ubuntu:12.04/precise-updates [i386]) for 'libdrm-nouveau1a:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libgl1-mesa-dev'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libgl1-mesa-dri'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libgl1-mesa-dri:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libgl1-mesa-glx'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libgl1-mesa-glx:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libglapi-mesa:i386' because of 'libgl1-mesa-glx:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libglapi-mesa'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libglapi-mesa:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libglu1-mesa'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libglu1-mesa:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libglu1-mesa-dev'
Selected version '2.4.46-1ubuntu0.0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'libkms1'
Selected version '1.1.0-2ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'libmtdev1'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libosmesa6'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libosmesa6:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libosmesa6-dev'
Selected version '0.12.902-1ubuntu0.2' (Ubuntu:12.04/precise-updates [amd64]) for 'libpciaccess0'
Selected version '0.12.902-1ubuntu0.2' (Ubuntu:12.04/precise-updates [i386]) for 'libpciaccess0:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libxatracker1'
Selected version '1.79.9' (Ubuntu:12.04/precise-updates [all]) for 'linux-firmware'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [i386]) for 'linux-generic-pae:i386'
Selected version '3.5.0-18.29~precise1' (Ubuntu:12.04/precise-updates [all]) for 'linux-headers-3.5.0-18'
Selected version '3.5.0-18.29~precise1' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-headers-3.5.0-18-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-headers-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [i386]) for 'linux-headers-generic-pae:i386'
Selected version '3.5.0-18.29~precise1' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-image-3.5.0-18-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-image-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [i386]) for 'linux-image-generic-pae:i386'
Selected version '3.2.0-59.90' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-libc-dev'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'mesa-common-dev'
Selected version '8.0.1+git20110129+d8f7d6b-0ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'mesa-utils'
Selected version '331.20-0ubuntu0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'nvidia-331'
Selected version '331.20-0ubuntu0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'nvidia-settings'
Selected version '7.6+5ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'x11-apps'
Selected version '2.8-1~precise2' (Ubuntu:12.04/precise-updates [all]) for 'x11proto-dri2-dev'
Selected version '1.4.16-1~precise2' (Ubuntu:12.04/precise-updates [all]) for 'x11proto-gl-dev'
Selected version '1.4.0+git20120101.is.really.1.4.0-0ubuntu1~precise2' (Ubuntu:12.04/precise-updates [all]) for 'x11proto-randr-dev'
Selected version '2:1.11.4-0ubuntu10.14' (Ubuntu:12.04/precise-updates [all]) for 'xserver-common'
Selected version '2:1.11.4-0ubuntu10.14' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-core'
Selected version '1:2.7.0-0ubuntu1.2' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-evdev'
Selected version '1:1.7.1-1build3' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-input-mouse'
Selected version '1.6.2-1ubuntu1~precise2' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-synaptics'
Selected version '1:12.9.0-0ubuntu0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-vmmouse'
Selected version '1:0.14.0-0ubuntu2.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-wacom'
Selected version '1:1.2.3-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-apm'
Selected version '1:0.7.3-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-ark'
Selected version '1:6.14.99~git20111219.aacbd629-0ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-ati'
Selected version '1:1.2.4-1build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-chips'
Selected version '1:1.3.2-4build1' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-cirrus'
Selected version '1:0.4.2-4ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-fbdev'
Selected version '2.11.13-2build1' (Ubuntu:12.04/precise [i386]) for 'xserver-xorg-video-geode:i386'
Selected version '1:1.3.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-i128'
Selected version '1:1.3.2-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-i740'
Selected version '2:2.17.0-1ubuntu4.4' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-intel'
Selected version '6.9.0-1build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-mach64'
Selected version '1:1.4.13.dfsg-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-mga'
Selected version '1:1.2.5-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-neomagic'
Selected version '1:0.0.16+git20111201+b5534a1-1build3' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-nouveau'
Selected version '1:0.2.904+svn1050-1ubuntu0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-openchrome'
Selected version '0.0.16-2ubuntu0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-qxl'
Selected version '6.8.1-5build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-r128'
Selected version '1:6.14.99~git20111219.aacbd629-0ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-radeon'
Selected version '1:4.2.4-2ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-rendition'
Selected version '1:0.6.3-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-s3'
Selected version '1:1.10.4-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-s3virge'
Selected version '1:2.3.3-1ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-savage'
Selected version '1:1.7.5-1build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-siliconmotion'
Selected version '1:0.10.3-3build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-sis'
Selected version '1:0.9.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-sisusb'
Selected version '1:1.4.3-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-tdfx'
Selected version '1:1.3.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-trident'
Selected version '1:1.2.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-tseng'
Selected version '1:2.3.0-7build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-vesa'
Selected version '1:12.0.1-1ubuntu1.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-vmware'
Selected version '1:1.2.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-voodoo'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-headers-generic-pae:i386 : Depends: linux-headers-3.2.0-59-generic-pae:i386 but it is not going to be installed
 mesa-common-dev : Depends: libdrm-dev (>= 2.4.19)
 xserver-xorg-video-geode:i386 : Depends: xorg-video-abi-11:i386
                                 Depends: xserver-xorg-core:i386 (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.
/usr/sbin/ppa-purge: line 180: aptitude: command not found
Warning:  Something went wrong, packages may not have been reverted
scott@scott-P5QC:~$ 

```

---

### Post by monkeybrain20122 on 2014-02-22
I think you have already broken your system when you first tried to upgrade, something has changed. You should have purged the ppa  BEFORE you upgrade. Not after it is aborted with errors. I wouldn't even waste my time trying to figure that out. Like I said if I do a clean install now by the time you figure this out I would have already playing with 14.04 for hours. ;)

---

### Post by ventrical on 2014-02-22
> **monkeybrain20122 said:**
> I think you have already broken your system when you first tried to upgrade, something has changed. You should have purged the ppa  BEFORE you upgrade. Not after it is aborted with errors. I wouldn't even waste my time trying to figure that out. Like I said if I do a clean install now by the time you figure this out I would have already playing with 14.04 for hours. ;)


That is part of why we are here in U+1 testing. To figure out diffcult problems with installs:)lol

---

### Post by monkeybrain20122 on 2014-02-22
> **ventrical said:**
> That is part of why we are here in U+1 testing. To figure out diffcult problems with installs:)lol

But OP is not doing testing (not his intention anyway). He has been having issues with his graphic driver and wants to upgrade to 14.04 as his main (only) system.

---

### Post by sdowney717 on 2014-02-22
> **ventrical said:**
> That is part of why we are here in U+1 testing. To figure out diffcult problems with installs:)lol

So anything else to try?
or
Give up.

Update to new version, it resets the software channels automatically, never had to remove ppa before.

---

### Post by monkeybrain20122 on 2014-02-22
My guess is that  *parts* of your software channel are already reset in your first failed attempt hence so many packages have unmet dependencies. You are now in a hybrid mode. So if you insist on trouble shooting this you may inspect your sources and manually change everything back to Precise and provided that nothing else has changed ( like things being installed and removed) you may be able to purge your ppa.

If you have been able to upgrade before without purging ppas (that involves downgrading the packages, not just unlisting them) you might have been lucky as many people have problems, just take a look at all the broken upgrade threads and threads on issues that can be eventually traced back to upgrade. Or you might actually have problems without knowing it, upgrade seemed to have worked, but later manifested as strange problems that seem to be the themes of many of your threads.

Also don't forget that 14.04 is pre beta (or beta?)

---

### Post by zika on 2014-02-22
> **sdowney717 said:**
> Ok, reenabled it and something went wrong

So what to do?
```
Disabling xorg-edgers PPA from 
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list
Updating packages lists
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [amd64]) for 'libcairo2'
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [i386]) for 'libcairo2:i386'
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [amd64]) for 'libcairo-gobject2'
Selected version '1.10.2-6.1ubuntu3' (Ubuntu:12.04/precise-updates [i386]) for 'libcairo-gobject2:i386'
Selected version '2.4.46-1ubuntu0.0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'libdrm-nouveau1a'
Selected version '2.4.46-1ubuntu0.0.0.1' (Ubuntu:12.04/precise-updates [i386]) for 'libdrm-nouveau1a:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libgl1-mesa-dev'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libgl1-mesa-dri'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libgl1-mesa-dri:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libgl1-mesa-glx'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libgl1-mesa-glx:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libglapi-mesa:i386' because of 'libgl1-mesa-glx:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libglapi-mesa'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libglapi-mesa:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libglu1-mesa'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libglu1-mesa:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libglu1-mesa-dev'
Selected version '2.4.46-1ubuntu0.0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'libkms1'
Selected version '1.1.0-2ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'libmtdev1'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libosmesa6'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [i386]) for 'libosmesa6:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libosmesa6-dev'
Selected version '0.12.902-1ubuntu0.2' (Ubuntu:12.04/precise-updates [amd64]) for 'libpciaccess0'
Selected version '0.12.902-1ubuntu0.2' (Ubuntu:12.04/precise-updates [i386]) for 'libpciaccess0:i386'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'libxatracker1'
Selected version '1.79.9' (Ubuntu:12.04/precise-updates [all]) for 'linux-firmware'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [i386]) for 'linux-generic-pae:i386'
Selected version '3.5.0-18.29~precise1' (Ubuntu:12.04/precise-updates [all]) for 'linux-headers-3.5.0-18'
Selected version '3.5.0-18.29~precise1' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-headers-3.5.0-18-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-headers-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [i386]) for 'linux-headers-generic-pae:i386'
Selected version '3.5.0-18.29~precise1' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-image-3.5.0-18-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-image-generic'
Selected version '3.2.0.59.70' (Ubuntu:12.04/precise-updates [i386]) for 'linux-image-generic-pae:i386'
Selected version '3.2.0-59.90' (Ubuntu:12.04/precise-updates [amd64]) for 'linux-libc-dev'
Selected version '8.0.4-0ubuntu0.7' (Ubuntu:12.04/precise-updates [amd64]) for 'mesa-common-dev'
Selected version '8.0.1+git20110129+d8f7d6b-0ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'mesa-utils'
Selected version '331.20-0ubuntu0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'nvidia-331'
Selected version '331.20-0ubuntu0.0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'nvidia-settings'
Selected version '7.6+5ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'x11-apps'
Selected version '2.8-1~precise2' (Ubuntu:12.04/precise-updates [all]) for 'x11proto-dri2-dev'
Selected version '1.4.16-1~precise2' (Ubuntu:12.04/precise-updates [all]) for 'x11proto-gl-dev'
Selected version '1.4.0+git20120101.is.really.1.4.0-0ubuntu1~precise2' (Ubuntu:12.04/precise-updates [all]) for 'x11proto-randr-dev'
Selected version '2:1.11.4-0ubuntu10.14' (Ubuntu:12.04/precise-updates [all]) for 'xserver-common'
Selected version '2:1.11.4-0ubuntu10.14' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-core'
Selected version '1:2.7.0-0ubuntu1.2' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-evdev'
Selected version '1:1.7.1-1build3' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-input-mouse'
Selected version '1.6.2-1ubuntu1~precise2' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-synaptics'
Selected version '1:12.9.0-0ubuntu0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-vmmouse'
Selected version '1:0.14.0-0ubuntu2.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-input-wacom'
Selected version '1:1.2.3-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-apm'
Selected version '1:0.7.3-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-ark'
Selected version '1:6.14.99~git20111219.aacbd629-0ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-ati'
Selected version '1:1.2.4-1build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-chips'
Selected version '1:1.3.2-4build1' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-cirrus'
Selected version '1:0.4.2-4ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-fbdev'
Selected version '2.11.13-2build1' (Ubuntu:12.04/precise [i386]) for 'xserver-xorg-video-geode:i386'
Selected version '1:1.3.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-i128'
Selected version '1:1.3.2-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-i740'
Selected version '2:2.17.0-1ubuntu4.4' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-intel'
Selected version '6.9.0-1build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-mach64'
Selected version '1:1.4.13.dfsg-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-mga'
Selected version '1:1.2.5-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-neomagic'
Selected version '1:0.0.16+git20111201+b5534a1-1build3' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-nouveau'
Selected version '1:0.2.904+svn1050-1ubuntu0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-openchrome'
Selected version '0.0.16-2ubuntu0.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-qxl'
Selected version '6.8.1-5build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-r128'
Selected version '1:6.14.99~git20111219.aacbd629-0ubuntu2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-radeon'
Selected version '1:4.2.4-2ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-rendition'
Selected version '1:0.6.3-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-s3'
Selected version '1:1.10.4-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-s3virge'
Selected version '1:2.3.3-1ubuntu1' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-savage'
Selected version '1:1.7.5-1build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-siliconmotion'
Selected version '1:0.10.3-3build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-sis'
Selected version '1:0.9.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-sisusb'
Selected version '1:1.4.3-4build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-tdfx'
Selected version '1:1.3.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-trident'
Selected version '1:1.2.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-tseng'
Selected version '1:2.3.0-7build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-vesa'
Selected version '1:12.0.1-1ubuntu1.1' (Ubuntu:12.04/precise-updates [amd64]) for 'xserver-xorg-video-vmware'
Selected version '1:1.2.4-2build2' (Ubuntu:12.04/precise [amd64]) for 'xserver-xorg-video-voodoo'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-headers-generic-pae:i386 : Depends: linux-headers-3.2.0-59-generic-pae:i386 but it is not going to be installed
 mesa-common-dev : Depends: libdrm-dev (>= 2.4.19)
 xserver-xorg-video-geode:i386 : Depends: xorg-video-abi-11:i386
                                 Depends: xserver-xorg-core:i386 (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.
/usr/sbin/ppa-purge: line 180: aptitude: command not found
Warning:  Something went wrong, packages may not have been reverted
scott@scott-P5QC:~$ 

```It seems that ppa-purge need aptitude in Your version. Just install aptitude and retry whole thing. Try, after that```
sudo apt-get install -f
```...
It looks scary but it is not now... I'd bet... Just a glitch with aptitude not being present...

---

### Post by zika on 2014-02-22
> **monkeybrain20122 said:**
> My guess is that  *parts* of your software channel are already reset in your first failed attempt hence so many packages have unmet dependencies. You are now in a hybrid mode. So if you insist on trouble shooting this you may inspect your sources and manually change everything back to Precise and provided that nothing else has changed ( like things being installed and removed) you may be able to purge your ppa.

If you have been able to upgrade before without purging ppas (that involves downgrading the packages, not just unlisting them) you might have been lucky as many people have problems, just take a look at all the broken upgrade threads and threads on issues that can be eventually traced back to upgrade. Or you might actually have problems without knowing it, upgrade seemed to have worked, but later manifested as strange problems that seem to be the themes of many of your threads.Nothing from next version should have infiltrated yet because only calculating of upgrade was interrupted...

---

### Post by monkeybrain20122 on 2014-02-22
> **zika said:**
> It seems that ppa-purge need aptitude in Your version. Just install aptitude and retry whole thing. Try, after that```
sudo apt-get install -f
```...
It looks scary but it is not now... I'd bet... Just a glitch with aptitude not being present...

How about
```
The following packages have unmet dependencies:
 linux-headers-generic-pae:i386 : Depends: linux-headers-3.2.0-59-generic-pae:i386 but it is not going to be installed
 mesa-common-dev : Depends: libdrm-dev (>= 2.4.19)
 xserver-xorg-video-geode:i386 : Depends: xorg-video-abi-11:i386
                                 Depends: xserver-xorg-core:i386 (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.
```

Doesn't sound like just an aptitude glitch. Why is linux-headers-3.2 not going to be installed? OP can try to install one of these in the terminal and the error message will give some clues as to what actually happens.

---

### Post by 23dornot23d on 2014-02-22
If you do the following what list does it give you - and what dependencies are a problem ........
If aptitude is working ......

```


sudo sed -i s'/precise/trusty/g' /etc/apt/sources.list

aptitude update
aptitude dist-upgrade


```


As a example and I always do things on my own machine first - it will come back with a listing like this

```

root@keith-laptop:/home/keith# aptitude dist-upgrade
The following NEW packages will be installed:
  erlang-mnesia{a} fonts-pagul{a} hardening-includes{a} 
  libemail-abstract-perl{a} libemail-date-format-perl{a} 
  libemail-messageid-perl{a} libemail-mime-contenttype-perl{a} 
  libemail-mime-perl{a} libemail-send-io-perl{a} libemail-send-perl{a} 
  libemail-simple-perl{a} libgmime2.6-cil{a} libgtk-vnc-2.0-0{a} 
  libgtk2-appindicator-perl{a} libgvnc-1.0-0{a} libio-all-perl{a} 
  libiso9660-8{a} libjs-sphinxdoc{a} libjs-underscore{a} liblept4{a} 
  liblightdm-qt-3-0{a} libmime-types-perl{a} libminiupnpc8{a} 
  libmodemmanagerqt1{a} libmouse-perl{a} libmro-compat-perl{a} 
  libnatpmp1{a} libnet-dropbox-api-perl{a} libnet-oauth-perl{a} 
  libnetworkmanagerqt1{a} libperl4-corelibs-perl{a} libperlio-gzip-perl{a} 
  libprotoc8{a} libreturn-value-perl{a} libruby1.9.1{a} libspiffy-perl{a} 
  libswt-cairo-gtk-3-jni{a} libswt-gnome-gtk-3-jni{a} 
  libswt-webkit-gtk-3-jni{a} libtesseract3{a} libtext-levenshtein-perl{a} 
  libunicap2{a} libxine2{a} libxine2-bin{a} libxine2-doc{a} 
  libxine2-ffmpeg{a} libxine2-misc-plugins{a} libxine2-plugins{a} 
  libxine2-x{a} libxml-commons-external-java{a} 
  libxml-commons-resolver1.1-java{a} linux-headers-3.13.0-11{a} 
  linux-headers-3.13.0-11-generic{a} linux-image-extra-3.13.0-11-generic{a} 
  mjpegtools-gtk{a} onboard-data{a} osspd{ab} osspd-pulseaudio{a} 
  plasma-nm{a} python-commandnotfound{a} python-debianbts{a} python-pil{a} 
  python3-chardet{a} python3-debian{a} python3-six{a} ruby-atk{a} 
  ruby-gdk-pixbuf2{a} ruby-glib2{a} ruby-pango{a} ruby1.9.1{a} t1utils{a} 
  tesseract-ocr-equ{a} tesseract-ocr-osd{a} ubuntu-wallpapers-saucy 
  unity-settings-daemon{a} xbrlapi{a} 
The following packages will be upgraded:
  adium-theme-ubuntu backintime-common backintime-gnome bbswitch-dkms 
  brltty brltty-x11 casper cdrdao create-resources cups-pk-helper dcraw 
  debootstrap dos2unix dvgrab erlang-asn1 erlang-base-hipe erlang-crypto 
  erlang-esdl erlang-gs erlang-runtime-tools erlang-syntax-tools 
  evolution-indicator fancontrol folks-common games-thumbnails 
  gir1.2-folks-0.6 gir1.2-javascriptcoregtk-3.0 gir1.2-networkmanager-1.0 
  gir1.2-webkit-3.0 gir1.2-xkl-1.0 gnome-exe-thumbnailer gnome-shell 
  gnome-shell-common gtk2-engines-qtcurve gtkpod gtkpod-data hddtemp 
  indicator-sound inputattach kbattleship kde-style-qtcurve kde-zeroconf 
  kdegraphics-strigi-plugins kdm-theme-aperture kdm-theme-bespin 
  kdm-theme-tibanna kino ksaneplugin ktron language-pack-en 
  language-pack-es language-pack-gnome-en language-pack-gnome-es 
  language-pack-gnome-pt language-pack-gnome-xh language-pack-pt 
  language-pack-xh libatk1-ruby1.8 libcap2 libcap2-bin 
  libconfig-inifiles-perl libdatetime-format-mail-perl 
  libdatetime-format-w3cdtf-perl libdevel-symdump-perl libdlrestrictions1 
  libdom4j-java libdynamite0 libegl1-mesa libegl1-mesa-dev 
  libegl1-mesa-drivers libemail-address-perl libemail-find-perl 
  libemail-mime-encodings-perl libemail-valid-perl libevent-1.4-2 
  libevent-execflow-perl libevent-rpc-perl libextutils-depends-perl 
  libextutils-pkgconfig-perl libffi-dev libfile-find-rule-perl 
  libfile-slurp-perl libfile-which-perl libfolks-eds25 libfolks-telepathy25 
  libfolks25 libgbm-dev libgbm1 libgconfmm-2.6-1c2 libgda-5.0-4 
  libgda-5.0-common libgdata-common libgdata13 libgdiplus 
  libgdk-pixbuf2-ruby1.8 libgetopt-java libgl1-mesa-dev libgl1-mesa-dri 
  libgl1-mesa-glx libglademm-2.4-1c2a libgladeui-1-11 libglapi-mesa libgle3 
  libgles2-mesa libgles2-mesa-dev libglib2-ruby1.8 libglib2.0-doc 
  libgnome-menu2 libgnomevfs2-extra libgoffice-0.8-8 
  libgoffice-0.8-8-common libgoocanvas-common libgoocanvas3 libgpod-common 
  libgraphicsmagick++3 libgraphicsmagick3 libgraphite3 libgtk-vnc-1.0-0 
  libgtk2-ex-formfactory-perl libgtk2.0-doc libgtkhtml-editor-common 
  libgtkhtml-editor0 libgtkhtml3.14-19 libgtkimageview0 libhtml-format-perl 
  libhtml-fromtext-perl libhtml-tableextract-perl 
  libhttp-cache-transparent-perl libhyphen0 libibverbs1 libifp4 
  libintl-perl libio-socket-inet6-perl libio-string-perl libipc-run-perl 
  libiptcdata0 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 
  libjaxen-java libjaxme-java libjaxp1.3-java libjdom1-java libjson-perl 
  libkasten2controllers2abi1 libkasten2core2 libkasten2gui2 
  libkasten2okteta1controllers1abi1 libkasten2okteta1core1 
  libkasten2okteta1gui1 libkde4-ruby libkde4-ruby1.8 libksane0 
  libktorrent-l10n liblingua-preferred-perl liblog-tracemessages-perl 
  liblrdf0 liblua50 liblualib50 libming1 libmission-control-plugins0 
  libmldbm-perl libmlt-data libmono-cairo2.0-cil libmono-cecil-private-cil 
  libmono-i18n-west2.0-cil libmono-i18n-west4.0-cil 
  libmono-management2.0-cil libmono-management4.0-cil 
  libmono-messaging2.0-cil libmono-sharpzip2.84-cil libmono-simd2.0-cil 
  libmono-system-messaging2.0-cil 
  libmono-system-runtime-serialization-formatters-soap4.0-cil 
  libmono-system-runtime2.0-cil libmono-system-runtime4.0-cil 
  libmono-system-security4.0-cil 
  libmono-system-web-applicationservices4.0-cil libmono-web4.0-cil 
  libmozjs185-1.0 libmythes-1.2-0 libnet-domain-tld-perl libnet-ip-perl 
  libnetpbm10 libnm-glib-vpn1 libnm-glib4 libnm-util2 libnotify-bin 
  libnss-mdns libnumber-compare-perl libogg-vorbis-header-pureperl-perl 
  libokteta1core1 libokteta1gui1 libopenobex1 libopenvg1-mesa 
  libossp-uuid16 libotr2 libpam-ck-connector libpango1-ruby1.8 
  libpango1.0-doc libpaper-utils libparse-debcontrol-perl 
  libparse-debianchangelog-perl libparse-recdescent-perl libpath-class-perl 
  libpathplan4 libpeas-common libplymouth2 libpod-coverage-perl 
  libpolkit-qt-1-1 libpostproc52 libpq5 libproc-simple-perl libpsiconv6 
  libpthread-stubs0-dev libpurple-bin libqapt2 libqapt2-runtime 
  libqca2-plugin-ossl libqdox-java libqhull5 libqt4-ruby1.8 libqt4-webkit 
  libqtruby4shared2 librarian0 librecad librecad-data libregexp-common-perl 
  libregexp-java libresid-builder0c2a libruby1.8 libservlet2.5-java 
  libsexy2 libsidplay2 libslp1 libsmokebase3 libsmokekdecore4-3 
  libsmokekdeui4-3 libsmokekfile3 libsmokekhtml3 libsmokekio3 
  libsmokeknewstuff2-3 libsmokeknewstuff3-3 libsmokekparts3 
  libsmokektexteditor3 libsmokekutils3 libsmokenepomuk3 libsmokephonon3 
  libsmokeplasma3 libsmokeqtcore4-3 libsmokeqtdbus4-3 libsmokeqtgui4-3 
  libsmokeqtnetwork4-3 libsmokeqtopengl4-3 libsmokeqtscript4-3 
  libsmokeqtsql4-3 libsmokeqtsvg4-3 libsmokeqttest4-3 libsmokeqtuitools4-3 
  libsmokeqtwebkit4-3 libsmokeqtxml4-3 libsmokesolid3 libsnmp-base 
  libsox-fmt-all libsox-fmt-ao libsox-fmt-mp3 libsox-fmt-oss 
  libsox-fmt-pulse libsqlite0 libsys-hostname-long-perl 
  libterm-progressbar-perl libtest-pod-perl libtext-glob-perl libtheora-bin 
  libtie-ixhash-perl libtiff-tools libtimezonemap1 libtommath0 libtool 
  libtorque2 libunique-3.0-0 libuser-perl libvcdinfo0 libvirtodbc0 
  libvisual-0.4-plugins libwebkit1.1-cil libwebkit2gtk-3.0-25 
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwebkitgtk-3.0-0 
  libwebkitgtk-3.0-common libweed0 libwmf-bin libwsutil-dev 
  libwww-search-perl libx11-protocol-perl libxatracker2 libxbase2.0-0 
  libxdot4 libxerces2-java libxfce4util-bin libxine1 libxine1-bin 
  libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-x 
  libxklavier16 libxml-regexp-perl libxml-rss-perl libxml-twig-perl 
  libxml-writer-perl libxml2-utils libxmltv-perl libxmmsclient-glib1 
  libxmmsclient6 libxom-java libxpp2-java libzip2 light-themes 
  lightdm-kde-greeter lintian linux-generic linux-headers-generic 
  linux-image-generic linux-libc-dev lirc lives lives-data lksctp-tools 
  lm-sensors localechooser-data locales lokalize lp-solve lsdvd 
  lupin-casper lxappearance lxde lxde-common lxde-core lxde-icon-theme 
  lxinput lxmusic lxrandr lxsession-edit lxshortcut lzma-dev manpages-dev 
  mdf2iso medit meld mencoder mesa-common-dev mjpegtools mkvtoolnix 
  mobile-broadband-provider-info modemmanager module-assistant mono-2.0-gac 
  monodoc-base monodoc-browser monodoc-manual mousetweaks mp3gain mpg123 
  mpg321 mplayer mppenc mscompress mtools mypaint mypaint-data 
  nautilus-actions nautilus-sendto netpbm network-manager 
  network-manager-gnome network-manager-pptp network-manager-pptp-gnome 
  notify-osd-icons obconf obex-data-server obexd-client okteta omniidl 
  onboard openprinting-ppds optipng orage os-prober oss-compat p11-kit 
  p7zip paman pavucontrol pavumeter pbuilder pidgin-guifications 
  pidgin-libnotify pidgin-plugin-pack pidgin-sipe pinentry-gtk2 pitivi 
  plasma-scriptengine-python plasma-scriptengine-ruby 
  plasma-widget-message-indicator plasma-widget-networkmanagement 
  plasma-widgets-active plymouth plymouth-label plymouth-theme-ubuntu-logo 
  plymouth-theme-ubuntu-text plymouth-x11 policykit-desktop-privileges 
  polkit-kde-1 poxml pptp-linux preload protobuf-compiler 
  pulseaudio-esound-compat pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-gconf-dbg pulseaudio-module-x11 
  pulseaudio-module-x11-dbg pulseaudio-utils pyside-tools python-avahi 
  python-beautifulsoup python-bluez python-brlapi python-cairo-dev 
  python-chm python-configglue python-couchdb python-cups 
  python-cupshelpers python-dateutil python-defer python-desktop-agnostic 
  python-egenix-mxdatetime python-egenix-mxtools python-enchant 
  python-feedparser python-fpconst python-gdbm python-gmenu 
  python-gnomekeyring python-gnupginterface python-gobject-2-dev 
  python-gtk-vnc python-gtk2-dev python-gtk2-doc python-gtkspell 
  python-ibus python-imaging python-iniparse python-levenshtein 
  python-libproxy python-louis python-lxml python-mako python-markupsafe 
  python-notify python-opengl python-openssl python-pam python-paramiko 
  python-pexpect python-ply python-protobuf python-pyasn1 python-pyexiv2 
  python-pygoocanvas python-pyicu python-pyinotify python-pyside 
  python-pyside.phonon python-pyside.qtcore python-pyside.qtdeclarative 
  python-pyside.qtgui python-pyside.qthelp python-pyside.qtnetwork 
  python-pyside.qtopengl python-pyside.qtscript python-pyside.qtsql 
  python-pyside.qtsvg python-pyside.qttest python-pyside.qtuitools 
  python-pyside.qtwebkit python-pyside.qtxml python-rdflib python-reportbug 
  python-reportlab python-reportlab-accel python-rsvg python-serial 
  python-smbc python-telepathy python-twisted python-twisted-conch 
  python-twisted-lore python-twisted-mail python-twisted-names 
  python-twisted-news python-twisted-runner python-twisted-web 
  python-twisted-words python-uniconvertor python-utidylib python-virtkey 
  python-vobject python-vte python-webkit python-webkit-dev python-wnck 
  python-wxgtk2.8 python-wxversion qapt-batch qhull-bin qt4-doc 
  qtcreator-doc radeontool rarian-compat rdate rdesktop reiserfsprogs 
  reportbug rlwrap rtkit ruby ruby-cairo ruby-kde4 ruby-phonon ruby-plasma 
  ruby-qt4 ruby-qt4-script ruby-qt4-test ruby-qt4-uitools ruby-qt4-webkit 
  ruby1.8 sane-utils sbackup screen-resolution-extra sessioninstaller 
  setserial shutter simple-scan smartdimmer snacc snacc-doc socat speex 
  squashfs-tools ssh-askpass-gnome swh-plugins sysinfo syslinux 
  syslinux-common system-config-printer-common system-config-printer-gnome 
  system-config-printer-udev tango-icon-theme tango-icon-theme-common 
  telepathy-gabble telepathy-haze telepathy-idle telepathy-logger 
  telepathy-mission-control-5 telepathy-salut tesseract-ocr 
  tesseract-ocr-eng thunar-volman tidy tomboy toshset transfig 
  translate-toolkit transmission-common transmission-gtk ttf-bengali-fonts 
  ttf-devanagari-fonts ttf-essays1743 ttf-gujarati-fonts ttf-indic-fonts 
  ttf-indic-fonts-core ttf-kannada-fonts ttf-lyx ttf-malayalam-fonts 
  ttf-oriya-fonts ttf-punjabi-fonts ttf-summersby ttf-tamil-fonts 
  ttf-telugu-fonts ttf-unfonts-extra tumbler tumbler-common tvtime twolame 
  ubuntu-artwork ubuntu-docs ubuntu-mono ubuntu-system-service 
  ubuntu-wallpapers umbrello unace unity-greeter unp unrar-free 
  usb-creator-common usb-creator-gtk user-setup valgrind vbetool vcdimager 
  vgabios vinagre vino virtualgl virtualgl-libs virtuoso-minimal 
  virtuoso-opensource-6.1-bin virtuoso-opensource-6.1-common vorbisgain 
  vuze w3m wamerican wavpack wbritish wdiff wine winetricks x11-apps 
  x11-session-utils x11-xfs-utils xaos xarchiver xcftools xchm 
  xdg-user-dirs xdg-user-dirs-gtk xfdesktop4 xfdesktop4-data xfonts-mathml 
  xfsprogs xfwm4 xine-ui xinit xinput xmltv-util xnest xorg xorg-docs-core 
  xplanet xplanet-images xscreensaver xserver-xephyr xserver-xorg 
  xserver-xorg-input-all xsltproc xtrans-dev yabause-common yabause-gtk 
  yarssr youtube-dl 
The following partially installed packages will be configured:
  vokoscreen{b} 
The following packages are RECOMMENDED but will NOT be installed:
  galculator libpam-cap padevchooser python-pyexiv2-doc rtmpdump 
  sbackup-gtk 
665 packages upgraded, 76 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.5 MB/474 MB of archives. After unpacking 258 MB will be used.
The following packages have unmet dependencies:
 vokoscreen : Depends: libav-tools but it is not going to be installed.
 osspd : Conflicts: oss-compat but 6 is to be installed.
 wings3d : Depends: erlang-abi-13.a which is a virtual package.
The following actions will resolve these dependencies:

     Remove the following packages:                       
1)     vokoscreen                                         
2)     wings3d                                            

     Keep the following packages at their current version:
3)     osspd [Not Installed]                              

     Leave the following dependencies unresolved:         
4)     oss-compat recommends osspd                        
5)     osspd-pulseaudio recommends osspd                  


Accept this solution? [Y/n/q/?] 


Just q to quit out of it ...........

```

BUT ANSWER NO TO THE DIST UPGRADE ........ ( Just want to see the list of problems it comes back with for now )


do the reverse afterwards to put it back to how it was ....... all we are doing is changing the package listings
then putting them back to how they originally were ...... doing some investigations first ..... before changing anything

```


sudo sed -i s'/trusty/precise/g' /etc/apt/sources.list
aptitude update


```

---

### Post by zika on 2014-02-22
> **monkeybrain20122 said:**
> How about
```
The following packages have unmet dependencies:
 linux-headers-generic-pae:i386 : Depends: linux-headers-3.2.0-59-generic-pae:i386 but it is not going to be installed
 mesa-common-dev : Depends: libdrm-dev (>= 2.4.19)
 xserver-xorg-video-geode:i386 : Depends: xorg-video-abi-11:i386
                                 Depends: xserver-xorg-core:i386 (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.
```

Doesn't sound like just an aptitude glitch. Why is linux-headers-3.2 not going to be installed? OP can try to install one of these in the terminal and the error message will give some clues as to what actually happens.I never said it is aptitude glitch because, as I can deduct from message OP've received, it is not, even, installed... If it is not installed it can not produce any glitch... ;)

---

### Post by ventrical on 2014-02-22
> **sdowney717 said:**
> So anything else to try?
or
Give up.

Update to new version, it resets the software channels automatically, never had to remove ppa before.


If you have the trusty daily .iso and want to install that and keep all of your bookmarks, etc.. then you can do an install through Ubiquity partitioner choosing 'something else'. Then , choose the partition/ change/ choose ext4 and root '/' but do not format. It will keep all of your files .. etc.. but will give you an error that 'some files may have to be re-installed'. it may wipe out all your ppas or it may keep them :). Thats up to you if you want to try it.

 Also ... try zika's suggestion and see what happens.

---

### Post by ventrical on 2014-02-22
> **monkeybrain20122 said:**
> But OP is not doing testing (not his intention anyway). He has been having issues with his graphic driver and wants to upgrade to 14.04 as his main (only) system.


Trusty .iso is designed now with abilty to bring in all important files on desktop  and /home/ if you use the Ubiquity partitioner and not format the partition to be installed upon. It's really a streamline breeze but I like to do CLI work-a-rounds and  it appears the OP is a veteran user of Ubuntu.. so perhaps OP is trying to exhaust all possibilities.

---

### Post by mc4man on 2014-02-22
As far as any problematic xserver-xorg-video packages, none mentioned yet  are needed on your hardware so maybe remove them.
Regarding the linux-headers - what is currently installed on your system?,  3.2.0-59 was at precise release, 3.2.0-60.91 is in precise-proposed
(assuming this is a release install vs. later 12.04 point releases which use lts packages

---

### Post by ventrical on 2014-02-22
Ok.. just thought of somthing.

Please report the results of 

```

lsb_release -a

```

---

### Post by ventrical on 2014-02-22
Then, if you are still using precise kernel I would:


[B]sudo sed -i 's/precise/trusty/g' /etc/apt/sources.list



Then:

[/B][B][B]sudo apt-get update && sudo apt-get dist-upgrade

[/B][/B] [B]sudo apt-get update

   sudo apt-get dist-upgrade


[/B]

---

### Post by 23dornot23d on 2014-02-22
See my previous post ......... do some checks before doing apt-get (upgrading) and getting into dependency hell .......


When upgrading - the system usually needs to be in a good state .......... and already as uptodate
on the previous system as can possibly be achieved.

But I find aptitude will do most of the hard work for you - finding and coming up
with solutions for dependency problems that often can be fixed easily by removing
some of the problematic things beforehand. With [COLOR=#ff0000]**aptitude dist-upgrade**[/COLOR] the system
will do its best to find a resolution ......... keep answering [COLOR=#ff0000]**no**[/COLOR] till it gives one that
satisfies you - and always check what it is wanting to remove.

By removing problematic things shown in the listing and then re-installing them 
after the .....

aptitude dist-upgrade ......... answer no ......... to see what other options it gives you 
back ( you can run this as many times as needed without actually changing anything )
just have a good look to see what all the options are first ........... often one will come
back where it needs to remove very few packages if any ( as it will often look for upgrade
options or downgrade packages to keep the system running ok )

When the final release of 14.04 comes out - then is the time to fully upgrade things.
But keep a working system upto that point ....... try not to destroy it by removing things or
by getting into dependency hell.

( I usually find I have a system that can be upgraded and made to work - without
running into reams of dependency problems. )

The latest upgrade I have done over the last 2 days went from 10.10 right upto 14.04.

As long as the configuration files do not get messed up along the way then things should
go smoothly ...... then its a case of when the final release comes out to do the full 
upgrade ......... [COLOR=#ff0000]**aptitude dist-upgrade**[/COLOR] and **[COLOR=#ff0000]aptitude safe-upgrade[/COLOR]** are system savers.

apt-get dist-upgrade ( is dependency hell ) 

I have rarely lost a system through upgrading using aptitude ........

and I rarely have to use apt-get -  from years of learning the hard way
only when aptitude does not work - do you need apt-get.

---

### Post by sdowney717 on 2014-02-22
I gave up on it, monkeybrain  was too discouraging.

I installed 13.10 and am now in process of upgrading to 14.04 and it is working so far.

I wrote down all the programs I want to use again.

We had a little bit of fun wondering what was up with it.

---

### Post by 23dornot23d on 2014-02-22
I sort of guessed from the time away - you must be re-installing 

at least you will have a totally clean system once installed ...... the problem

with upgrading is often packages get left behind that can cause headaches later on

I have about 20 distros on usb drives to choose from - sort of obsessed with finding

out what works best for graphics and making my enjoyment time easier.

The thing with upgrades is they usually do give problems - but I find my own 

approach to solving them now works a lot better than trusting apt-get upgrades

of any kind.

---

### Post by monkeybrain20122 on 2014-02-22
> **sdowney717 said:**
> I gave up on it, monkeybrain  was too discouraging.

I installed 13.10 and am now in process of upgrading to 14.04 and it is working so far.

I wrote down all the programs I want to use again.

We had a little bit of fun wondering what was up with it.

Well not trying to be negative, but if you want to solve a problem you have to first isolate the probable causes. You started with a graphic problem with some probable solutions, the way I would go about it would be to try the solutions in a way that would be most reversible (if possible) and if the solutions may bring in other issues make sure that they are at least tractable. A clean install and update your driver would be the way to go since it was decided that 12.04 may be too old. Why clean install? Because you can rule out complications due to upgrade and left over fragments from old system. Even if you successfully upgrade you can't be sure that it has not messed up anything. Upgrade has the potential of introducing issues on its own that are not even tractable, thus spawning more problems so I would advise against it,--in general and in particular in your case where the whole point is to solve a specific problem.

P.S. If you are reinstalling, why install 13.10 then upgrade to 14.04 instead of just keep 13.10 or install 14.04 directly? At the risk of being "discouraging" I would actually prefer keeping 13.10, because 14.04 is pre-beta or beta and once again there is a potential of spawning more problems rather than narrowing down the original one.

---

### Post by sdowney717 on 2014-02-22
libavcodec higher version in trusty.

I still have one problem, the hard drive gets beaten to death in ubuntu on this PC, with win7, that does not happen, not in the slightest.
I noticed that problem started a few months ago.
It's like the head is going all over the drive, whacking away and when it does that everything just grinds to a halt.

When I installed  13.10 after formatting the partition for the os of 20gb, it also still beats the drive. 
Is the drive fragmented?

Imagine running terminal and it takes a minute to load, meanwhile the drive is working hard.
Then while running installs in terminal, takes quite a while to do some simple things, like reading the database.

smart says its ok.

---

### Post by 23dornot23d on 2014-02-22
Run bootinfoscript and post the results back - see if it gives any clues

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sdowney717 on 2014-02-22
Lots there
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM 
                       /IO.SYS /MSDOS.SYS /COMMAND.COM

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu Trusty Tahr (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20120131
    Boot sector info:  Syslinux looks at sector 7150792 of /dev/sdc for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS
/dev/sda2         976,768,065 1,953,520,064   976,752,000  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   245,151,899   245,151,837   7 NTFS / exFAT / HPFS
/dev/sdb2         245,153,790 1,465,147,391 1,219,993,602   5 Extended
/dev/sdb5         842,551,296 1,465,147,391   622,596,096  83 Linux
/dev/sdb6         245,153,792   284,214,338    39,060,547  83 Linux
/dev/sdb7         284,217,344   292,028,415     7,811,072  82 Linux swap / Solaris
/dev/sdb8         292,030,464   842,549,247   550,518,784  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        0C3655E6635050E4                       ntfs       
/dev/sda2        36756aca-84d5-49d0-be11-1400329aabf1   ext4       
/dev/sdb1        26E82022E81FEEB5                       ntfs       
/dev/sdb5        0db1fb5a-0727-4347-bfa7-a551d8db6632   ext4       
/dev/sdb6        32e3119a-ca34-4876-b655-a74d70580f9f   ext4       
/dev/sdb7        388b3c4a-93a3-473c-89ec-77e8688e5845   swap       
/dev/sdb8        d7612b76-71df-4a33-8b17-6ae99f6f06e9   ext4       
/dev/sdc         2EB6-CB32                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /home                    ext4       (rw)
/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc         /media/scott/2EB6-CB32   vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=1
default=c:\
[operating systems]
c:\="Microsoft Windows" 
--------------------------------------------------------------------------------

=========================== sdb6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos 
insmod ext2
set root='hd1,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
else
  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=-1
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-32e3119a-ca34-4876-b655-a74d70580f9f' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos 
	insmod ext2
	set root='hd1,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
	else
	  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
	fi
	linux	/boot/vmlinuz-3.13.0-11-generic root=UUID=32e3119a-ca34-4876-b655-a74d70580f9f ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-11-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-32e3119a-ca34-4876-b655-a74d70580f9f' {
	menuentry 'Ubuntu, with Linux 3.13.0-11-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-11-generic-advanced-32e3119a-ca34-4876-b655-a74d70580f9f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos 
		insmod ext2
		set root='hd1,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
		else
		  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
		fi
		echo	'Loading Linux 3.13.0-11-generic ...'
		linux	/boot/vmlinuz-3.13.0-11-generic root=UUID=32e3119a-ca34-4876-b655-a74d70580f9f ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-11-generic-recovery-32e3119a-ca34-4876-b655-a74d70580f9f' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos 
		insmod ext2
		set root='hd1,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
		else
		  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
		fi
		echo	'Loading Linux 3.13.0-11-generic ...'
		linux	/boot/vmlinuz-3.13.0-11-generic root=UUID=32e3119a-ca34-4876-b655-a74d70580f9f ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-11-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-17-generic-advanced-32e3119a-ca34-4876-b655-a74d70580f9f' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos 
		insmod ext2
		set root='hd1,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
		else
		  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
		fi
		echo	'Loading Linux 3.11.0-17-generic ...'
		linux	/boot/vmlinuz-3.11.0-17-generic root=UUID=32e3119a-ca34-4876-b655-a74d70580f9f ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.11.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-17-generic-recovery-32e3119a-ca34-4876-b655-a74d70580f9f' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos 
		insmod ext2
		set root='hd1,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
		else
		  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
		fi
		echo	'Loading Linux 3.11.0-17-generic ...'
		linux	/boot/vmlinuz-3.11.0-17-generic root=UUID=32e3119a-ca34-4876-b655-a74d70580f9f ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.11.0-17-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos 
	insmod ext2
	set root='hd1,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
	else
	  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos 
	insmod ext2
	set root='hd1,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos6 --hint-efi=hd1,msdos6 --hint-baremetal=ahci1,msdos6  32e3119a-ca34-4876-b655-a74d70580f9f
	else
	  search --no-floppy --fs-uuid --set=root 32e3119a-ca34-4876-b655-a74d70580f9f
	fi
	knetbsd	/boot/memtest86+.elf console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-26E82022E81FEEB5' {
	insmod part_msdos 
	insmod ntfs
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  26E82022E81FEEB5
	else
	  search --no-floppy --fs-uuid --set=root 26E82022E81FEEB5
	fi
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb6 during installation
UUID=32e3119a-ca34-4876-b655-a74d70580f9f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=0db1fb5a-0727-4347-bfa7-a551d8db6632 /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=388b3c4a-93a3-473c-89ec-77e8688e5845 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdc/boot/grub/grub.cfg: ============================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz.efi  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdc/syslinux.cfg: ===============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

==================== sdc: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


================== sdc: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)


=============== sdc: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-Ihx8iF7y/Tmp_Log: No such file or directory
/home/scott/Downloads/bootscript/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
cat: /tmp/BootInfo-Ihx8iF7y/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-Ihx8iF7y/Tmp_Log: No such file or directory

```

---

### Post by 23dornot23d on 2014-02-22
It seems ok ..... was interested in the partitioning ....... all the start and end positions 
seem to be ok and you have smart disk and that reports ok .......

So not sure why it should be hunting around as you have just done a clean install ......


```

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu Trusty Tahr (development 
                       branch)
    Boot files:        /boot/grub/grub.cfg /etc/fstab


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   245,151,899   245,151,837   7 NTFS / exFAT / HPFS
/dev/sdb2         245,153,790 1,465,147,391 1,219,993,602   5 Extended
/dev/sdb5         842,551,296 1,465,147,391   622,596,096  83 Linux
/dev/sdb6         245,153,792   284,214,338    39,060,547  83 Linux
/dev/sdb7         284,217,344   292,028,415     7,811,072  82 Linux swap / Solaris
/dev/sdb8         292,030,464   842,549,247   550,518,784  83 Linux
```

No did not help really ........ but was worth the look .... just to understand the setup.

---

### Post by sdowney717 on 2014-02-22
yeah, irritating.
I counted the seconds just to load VLC, 25 seconds.
To load nautilus, about 4 seconds.
All from no prior activity.
VLC seems to take a very long time.

After it runs for awhile, seems better.

---

### Post by sdowney717 on 2014-02-22
One reason I upgraded was to try and improve VLC rendering of wtv video files from my win7 HTPC.
But the dropped frames are still there.
The VLC forum suggested my 12.04 was too old.

smplayer plays these perfect, silky, smooth.
VLC just terrible, painful to watch.
Same hardware in win7, vlc is perfect.

---

### Post by sdowney717 on 2014-02-22
I installed latest chrome stable and I cant use it.
It loads the prior cached pages ok.
BUT, click new tab, a new page loads and a second later the entire tab goes black. So stuck with firefox now.

Did that before I installed nvidia driver 331.38, and still doing it afterwards.

Ok reboot again, and now chrome is working. for now, but never know in future.

---

### Post by sdowney717 on 2014-02-22
```
vlc --reset-config
```
This fixed vlc playback of my wtv 1080p files, they are now smooth.

---

### Post by sdowney717 on 2014-02-22
After the VLC reset, takes 1 second to load VLC vs 25 seconds.

Everything has sped up for some reason.

---

