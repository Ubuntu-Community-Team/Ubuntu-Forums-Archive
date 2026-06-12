---
title: "Gnome-shell 3.31.90"
date: 2019-02-21
forum: Ubuntu Development Version
---

### Post by harry332 on 2019-02-21
Gnome-shell and mutter v. 3.31.90 are in proposed now. Mutter bump is from 3 to 4, so new gir1.2-mutter-4 and libmutter-4-0.
These work just fine. Now the top bar stays black.

---

### Post by jbicha on 2019-02-21
> Now the top bar stays black.

Ha, I have the opposite problem. My top bar stays purple!

---

### Post by dino99 on 2019-02-21
Hopes to get the 'extensions' upgraded soon too for compatibility: actually, the upgrade of GS want to remove the 'extension' packages.

My preferred:
[https://github.com/micheleg/dash-to-dock/issues](https://github.com/micheleg/dash-to-dock/issues)

---

### Post by corradoventu on 2019-02-22
new gnome-shell is in proposed but remains uninstalled```
The following packages have been kept back:
  cups cups-bsd cups-client cups-core-drivers cups-daemon cups-ipp-utils gnome-power-manager gnome-settings-daemon gnome-shell
  gnome-shell-common libcups2 libcupsimage2 libgl1-mesa-dri libsnmp30 lm-sensors mutter
The following packages will be upgraded:
  cups-browsed cups-filters cups-filters-core-drivers gir1.2-totem-1.0 gir1.2-udisks-2.0 gkbd-capplet
  gnome-shell-extension-ubuntu-dock gnome-software gnome-software-common gnome-software-plugin-snap inkscape libc-bin libc-dev-bin
  libc6 libc6-dbg libc6-dev libchamplain-0.12-0 libchamplain-gtk-0.12-0 libcupsfilters1 libfontembed1 libgnomekbd-common
  libgnomekbd8 libplymouth4 libpoppler-glib8 libtotem0 libtracker-control-2.0-0 libtracker-miner-2.0-0 libtracker-sparql-2.0-0
  libudisks2-0 locales multiarch-support mutter-common plymouth plymouth-label plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text poppler-utils totem totem-common totem-plugins tracker ubuntu-software udisks2 xfonts-base
44 upgraded, 1 newly installed, 0 to remove and 16 not upgraded.

```

---

### Post by harry332 on 2019-02-22
Corradoventu,
That is not good.
You have installed the new package mutter-common (likely also libmutter-4-0), but not the package mutter.
What are the unmet dependencies, if you only try to upgrade the package mutter?
And what are they if you then try to upgrade only gnome-shell and gnome-shell-common.

Then, I noticed you haven't upgraded the gnome-settings-daemon either. That (v. 3.30.2-2ubuntu1) is not in proposed anymore.
Try to upgrade those one by one, to find out what is wrong there.

---

### Post by corradoventu on 2019-02-22
Just done apt update+upgrade, Remember i'm using Disco with proposed so if some package has unmet dependencies this is NORMAL.

gnome-settings-daemon ```
corrado@corrado-p13-dd-1107-x:~$ apt policy gnome-settings-daemon
gnome-settings-daemon:
  Installed: 3.30.1.2-1ubuntu4
  Candidate: 3.30.2-2ubuntu1
  Version table:
     3.30.2-2ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
 *** 3.30.1.2-1ubuntu4 100
        100 /var/lib/dpkg/status
corrado@corrado-p13-dd-1107-x:~$ 

```

---

### Post by fthx on 2019-02-22
I use GNOME session, not Ubuntu.

Ok, I do not experience issues with GS 3.31.9x.
The only annoying bug is that I need to type my passwd to unlock the keyring at GS session startup.

@ Jeremy : My topbar is black.

I do not feel GS smoother than before => I keep the animations disabled for now... The new Adw theme is quite good (gtk+icons). Evolution needs to get refreshed toolbar icons.

---

### Post by jbicha on 2019-02-22
The translucent top bar is a [Yaru bug]("https://github.com/ubuntu/yaru/issues/1201") so it only affects the Ubuntu session.

The gnome-keyring bug is [LP: #1817128]("https://launchpad.net/bugs/1817128").

---

### Post by harry332 on 2019-02-23
Just like fthx, I am using gnome session only and with no issues.

Corradoventu,
you did not mention did you install g-s-d 3.30.2, mutter 3.31.90 and g-s 3.31.90
or which packages prevent you from doing this.

---

### Post by corradoventu on 2019-02-23
@harry332: as I said before I have not installed anything special, I'm just using Disco Dingo with the proposed and installing updates that come with apt update + upgrade.
if during development some packages lack of prerequisites I do not do unnecessary investigations. I can only wait for the problem to be solved by the developers
like for the problem in [https://ubuntuforums.org/showthread.php?t=2413188](https://ubuntuforums.org/showthread.php?t=2413188) (see jbicha's answer)
```
corrado@corrado-p13-dd-1107-x:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  cups cups-bsd cups-client cups-core-drivers cups-daemon cups-ipp-utils gnome-power-manager gnome-settings-daemon
  gnome-shell gnome-shell-common libcups2 libcupsimage2 libgl1-mesa-dri libsnmp30 lm-sensors mutter
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
corrado@corrado-p13-dd-1107-x:~$ 

```

---

### Post by dino99 on 2019-02-25
Feedback:

Got a dashtodock update, so i have also made the GS upgrade, and restarted the session: 
- even if the upgrade was done without error/warning, the dash icons have  gone (everything is ok inside tweaks)
- and systemmanager is also gone now. (tweaks error)

Feedback 2:
- downgraded GS and appindicator extension, and restarted the session.
- Dash icons (65) and systemmonitor are back as expected.

---

### Post by jbicha on 2019-02-25
Yes, based on the very small number of extensions I briefly [looked at]("https://community.ubuntu.com/t/monday-25th-february-2019/9959")  I expect most extensions that try to add an icon to the top bar will not work.

Since Dash to Dock and Ubuntu Dock share a similar base, it shouldn't be too difficult for someone to get Dash to Dock working.

Please report issues upstream for broken GNOME Shell extensions so that they can hopefully be fixed in time for Disco's release. Thanks!

---

### Post by corradoventu on 2019-03-06
New gnome-shell in proposed
```
corrado@corrado-p13-dd-0306:~$ apt policy gnome-shell
gnome-shell:
  Installed: 3.31.90-1ubuntu1
  Candidate: 3.31.90-1ubuntu1
  Version table:
 *** 3.31.90-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu disco-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     3.30.2-2ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
corrado@corrado-p13-dd-0306:~$ apt policy gnome-shell-extension-ubuntu-dock
gnome-shell-extension-ubuntu-dock:
  Installed: 64ubuntu4
  Candidate: 64ubuntu4
  Version table:
 *** 64ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu disco-proposed/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu disco-proposed/main i386 Packages
        100 /var/lib/dpkg/status
     64ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu disco/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu disco/main i386 Packages
corrado@corrado-p13-dd-0306:~$ 

```

---

### Post by harry332 on 2019-03-06
Actually the gnome-shell 3.31.90-1ubuntu1 is not new. It has been in proposed since 21th February.

---

### Post by harry332 on 2019-03-06
Now there is a new version of gnome-shell in proposed: 3.31.92-1ubuntu1
and of course new mutter too: 3.31.92-1~fakesync.
These both must be installed together.

If you install the newest gnome-settings-daemon (3.31.91-1ubuntu1) you also need the newest gnome-shell

Just tried all these and they are working just fine (gnome-session).

---

